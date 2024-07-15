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

# Geïndexeerde indexen zijn ongeldig en `indexer_reindex_all_invalid` worden constant uitgevoerd

Dit artikel biedt een mogelijke oplossing voor het probleem wanneer er voor uw site prestatieproblemen optreden die worden veroorzaakt door voortdurend opnieuw indexeren. Dit wordt veroorzaakt door de [!DNL cron] taak `indexer_reindex_all_invalid` die continu wordt uitgevoerd en caches die worden schoongemaakt op [!DNL reindex] .

## Betrokken producten en versies

* Adobe Commerce (cloud &amp; on-premisse) 2.4.0+ (Aangezien **[!UICONTROL Category Permissions]** een Adobe-Commerce-functie is, heeft dit geen invloed op de Magento Open Source.)

## Probleem

In [!DNL New Relic One] foutlogboeken moeten `indexer_update_all_views` vele keren worden weergegeven met een tijd > 1 seconde (dat wil zeggen dat het iets verwerkt).

## Oorzaak

Wanneer de belangrijkste Adobe Commerce-importer wordt uitgevoerd (handmatig of door [!DNL cron] ), wordt een set plug-ins voor meerdere kernmodules uitgevoerd om te bepalen welke indexen ongeldig moeten worden gemaakt.

De kwestie komt voor wanneer de **[!UICONTROL Category Permissions]** module in [!DNL Commerce Admin] wordt toegelaten. Als dit waar is, dan maakt de stop van de module altijd de indexen van het Product &amp; van de Categorie (en verbonden indexen) onbruikbaar wanneer het invoeren wordt uitgevoerd. Als de standaardimporttypen worden gecontroleerd, hebben ze allemaal invloed op **[!UICONTROL Category Permissions]** . Ongeldige validatie wordt verwacht.

Wanneer een site B2B-modules heeft ingeschakeld, wordt **[!UICONTROL Category Permissions]** ingeschakeld en vergrendeld als **[!UICONTROL Shared Catalog]** is geactiveerd. Als u **[!UICONTROL Shared Catalog]** uitschakelt, wordt **[!UICONTROL Category Permissions]** ontgrendeld, maar wordt dit niet uitgeschakeld.

<u> die [!DNL cron] controleert logboeken in uw [!DNL MySQL] gegevensbestand </u>:

Als u zich aanmeldt in uw [!DNL MySQL] -database, kunnen ze uw `cron` log controleren op het **[!DNL reindex all indexes]** -proces.
Dit **zou** vele malen moeten verschijnen, maar de belangrijke factor is dat het proces één van twee mogelijke dingen doet.

Het proces kan slechts één van deze twee dingen doen:

1. Niets: het zou 0 tot 1 seconde (één seconde of minder) duren - het proces controleert of het iets moet doen en dan stopt als het niets hoeft te doen.
1. [!DNL Reindex] alles: Het duurt altijd even - meestal minuten.

Normaal gesproken wilt u veel exemplaren van het proces zien, maar met een uitvoeringstijd van minder dan 1 seconde.
Een handelaar kan daarom deze [!DNL MySQL] vraag gebruiken om transacties te vinden die **meer dan 1 tweede** nemen om in werking te stellen:

```sql
SELECT TIMESTAMPDIFF(SECOND, executed_at, finished_at) AS period FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' HAVING period > 1
```

U kunt zien hoe lang een periode door loopt wordt geregistreerd:

```sql
SELECT executed_at FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' AND executed_at IS NOT NULL ORDER BY executed_at ASC LIMIT 1;
```

Als dit u niet lang genoeg geeft om een juiste beoordeling te maken, dan kunt u de tijd verhogen een succesvol `cron` proces in het logboek na deze [[!DNL Cron]  wordt gehouden (geplande taken) ](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) gids en het verhogen van de **[!DNL Success History Lifetime]** waarde (het gebrek is slechts 60 minuten).


## Oplossing

Breid `Magento\CatalogPermissions\Model\Indexer\Plugin\Import` uit, zodat de aangepaste importer niet wordt opgenomen in de methode `afterImportSource` .

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

Hierbij is `ENTITY_CODE` de waarde die wordt gebruikt voor de parameter entiteitsnaam in het `import.xml` -bestand voor de aangepaste importer.

## Gerelateerde lezing

[ vormt  [!DNL cron]  banen ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) in de Gids van de Configuratie van de Verrichtingen van Adobe Commerce.
