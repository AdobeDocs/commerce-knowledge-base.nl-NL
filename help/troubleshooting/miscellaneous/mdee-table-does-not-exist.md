---
title: Repareren gegevens niet bijgewerkt in  [!DNL Commerce Data Exporter]  voer en  [!DNL cron]  logboekfouten met veranderingslijst bestaan niet
description: Dit artikel verstrekt een oplossing voor het bevestigen van de kwesties van de gegevenssynchronisatie die door verkeerd meningsidentiteitskaart in  [!DNL Commerce Data Exporter mview]  abonnement te gebruiken worden veroorzaakt.
feature: Data Import/Export, Saas, Logs
role: Developer
source-git-commit: cf87b5f1280a2d1d23c7ace37616feb337b5142f
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Gegevens corrigeren die niet zijn bijgewerkt in [!DNL Commerce Data Exporter] feeds en [!DNL cron] -logfouten met een wijzigingstabel bestaan niet

Dit artikel verstrekt een oplossing om de kwesties van de gegevenssynchronisatie te bevestigen die door verkeerde meningsidentiteitskaart in het [!DNL Data Exporter] [[!DNL Mview] worden veroorzaakt ](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) abonnement te gebruiken. Het abonnement van [!DNL Mview] wordt gebruikt om wijzigingen voor databasetabellen bij te houden.

## Betrokken producten en versies

Adobe Commerce-instanties waarbij aangepaste code is toegepast op de functie voor het exporteren van gegevens ( `commerce-data-exporter` of `saas-exporter` ). De fout komt voor als de geïnstalleerde [[!DNL SaaS]  versie van de Uitvoer van Gegevens 103.3.0 ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes#release-6) of recenter is, en de code verwijst direct naar de `catalog_data_exporter_products` index.

## Probleem

Merchants kunnen vaststellen dat er in de tabellen met catalogusinvoer [!DNL Data Exporter] geen gegevens worden bijgewerkt. De volgende fouten worden dan weergegeven in de taaklogboeken van [!DNL cron] :

```
[2024-05-27T19:00:04.627604+00:00] report.ERROR: Cron Job indexer_clean_all_changelogs has an error: Table catalog_data_exporter_products_cl does not exist. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":305135616,"emalloc_start":283210384} [] [] 
```

## Oorzaak

Als gevolg van naamveranderingen in voederlijsten, indexen, en de lijsten van het veranderingslogboek in [!DNL Commerce Data Export] [ versie 103.3.0 ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes#release-9) versie, [!DNL Mview] abonnementen in douaneuitbreidingen die [!DNL Commerce Data Export] uitbreidingen gebruiken kunnen niet behoorlijk werken.

In dit geval, bestaat de *lijst niet* fout omdat de `catalog_data_exporter` lijstnaam in `cde_products_feed` werd veranderd, en u hebt douanecode die verwijzingen de oude naam in het [!DNL Data Exporter Mview] abonnement.

## Oplossing

Bewerk in de aangepaste extensie het configuratiebestand van [!DNL Mview] ( ```./etc/mview.xml``` ) om de tabelnaam `catalog_data_exporter_products` te wijzigen in *`cde_products_feed`* .

In het volgende voorbeeld ziet u de code die de tabellen opgeeft die worden bijgehouden door het abonnement van [!DNL Mview] :

```
<view id="cde_products_feed" class="Magento\CatalogDataExporter\Model\Indexer\ProductFeedIndexer" group="indexer">
     <subscriptions>
         <table name="custom_table" entity_column="product_id" />
     </subscriptions>
</view>
```

## Gerelateerde lezing

[[!DNL SaaS]  de Nota&#39;s van de Versie van de Uitbreiding van de Gegevens van de Uitvoer van Gegevens ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes) in de Gids van de Uitvoer van Gegevens van Adobe Commerce voor [!DNL SaaS] Diensten.
