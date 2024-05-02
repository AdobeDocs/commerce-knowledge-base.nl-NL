---
title: Geïndexeerde indexen en 'indexer_rendex_all_invalid` worden constant uitgevoerd
description: Geïndexeerde indexen en 'indexer_rendex_all_invalid` worden constant uitgevoerd
labels: troubleshooting,error,indexing,crons,site performance,adobe commerce,magento,cron,indexer_reindex_all_invalid,SQL,MySQL,reindex
exl-id: c7148ef4-2155-4d4c-869b-1d08de4af598
feature: B2B, Catalog Management, Categories, Observability, Price Indexer
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# Indexen ongeldig en `indexer_reindex_all_invalid` constant

Dit artikel biedt een mogelijke oplossing voor het probleem wanneer er voor uw site prestatieproblemen optreden die worden veroorzaakt door voortdurend opnieuw indexeren. Dit wordt veroorzaakt door de [!DNL cron] baan `indexer_reindex_all_invalid` continu draaiende caches en schoongemaakt op [!DNL reindex].

## Betrokken producten en versies

* Adobe Commerce (cloud &amp; on-premisse) 2.4.0+ (As **[!UICONTROL Category Permissions]** is een Adobe-Commerce-enige eigenschap, zal het geen Magento Open Source beïnvloeden.)

## Probleem

In [!DNL New Relic One] foutlogboeken moeten worden weergegeven `indexer_update_all_views` met een tijd van > 1 seconde (dat wil zeggen dat het iets verwerkt).

## Oorzaak

Wanneer de belangrijkste Adobe Commerce-importer wordt uitgevoerd (handmatig of door [!DNL cron]), dan wordt een reeks stop-ins over veelvoudige kernmodules uitgevoerd om te bepalen welke indexen ongeldig zouden moeten worden gemaakt.

De kwestie komt voor wanneer **[!UICONTROL Category Permissions]** module is ingeschakeld in de [!DNL Commerce Admin]. Als dit waar is, dan maakt de stop van de module altijd de indexen van het Product &amp; van de Categorie (en verbonden indexen) onbruikbaar wanneer het invoeren wordt uitgevoerd. Als de standaardinvoertypen worden onderzocht, hebben ze allemaal invloed op **[!UICONTROL Category Permissions]**. Ongeldige validatie wordt verwacht.

Wanneer een site B2B-modules heeft ingeschakeld, als **[!UICONTROL Shared Catalog]** wordt geactiveerd, wordt het ingeschakeld en vergrendelt **[!UICONTROL Category Permissions]**. Uitschakelen **[!UICONTROL Shared Catalog]** ontgrendelen **[!UICONTROL Category Permissions]**, maar schakel het niet uit.

<u>Controleren [!DNL cron] zich aanmeldt bij uw [!DNL MySQL] database</u>:

Als u zich aanmeldt bij uw [!DNL MySQL] database, kunnen ze uw `cron` log for the **[!DNL reindex all indexes]** proces.
Dit **moet** vaak voorkomen, maar het belangrijkste is dat het proces een van de twee mogelijke dingen doet.

Het proces kan slechts één van deze twee dingen doen:

1. Niets: het zou 0 tot 1 seconde (één seconde of minder) duren - het proces controleert of het iets moet doen en dan stopt als het niets hoeft te doen.
1. [!DNL Reindex] alles: Het zal altijd tijd vergen - meestal minuten.

Normaal gesproken wilt u veel exemplaren van het proces zien, maar met een uitvoeringstijd van minder dan 1 seconde.
Een handelaar kan deze [!DNL MySQL] vraag om transacties te vinden die nemen **meer dan 1 seconde** om uit te voeren:

```sql
SELECT TIMESTAMPDIFF(SECOND, executed_at, finished_at) AS period FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' HAVING period > 1
```

U kunt zien hoe lang een periode door loopt wordt geregistreerd:

```sql
SELECT executed_at FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' AND executed_at IS NOT NULL ORDER BY executed_at ASC LIMIT 1;
```

Als u hierdoor niet lang genoeg hebt om een juiste beoordeling te maken, kunt u de tijd verhogen `cron` het proces wordt gehouden in logboek volgend dit [[!DNL Cron] (geplande taken)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) de gids en het verhogen van **[!DNL Success History Lifetime]** waarde (de standaardwaarde is slechts 60 minuten).


## Oplossing

Uitbreiden `Magento\CatalogPermissions\Model\Indexer\Plugin\Import` zodat de `afterImportSource` wordt de aangepaste importmodule uitgesloten.

```
    public function afterImportSource(\Magento\ImportExport\Model\Import $subject, $import)
    {
        if ($this->config->isEnabled() && $subject->getEntity() !== 'ENTITY_CODE') {
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Category::INDEXER_ID)->invalidate();
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Product::INDEXER_ID)->invalidate();
        }
        return $import;
    }
```

Wanneer `ENTITY_CODE` is de waarde die wordt gebruikt voor de parameter voor de entiteitsnaam in het dialoogvenster `import.xml` bestand voor de aangepaste importmodule.

## Gerelateerde lezing

[Configureren [!DNL cron] banen](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) in de Adobe Commerce Operations Configuration Guide.
