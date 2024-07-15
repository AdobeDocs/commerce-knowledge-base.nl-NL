---
title: Het vallen terug naar  [!DNL Elasticsearch7]  wanneer de onderzoeksmotor aan  [!DNL Opensearch] wordt geplaatst
description: Dit artikel verstrekt een oplossing voor de kwestie wanneer a *Falling terug naar  [!DNL Elasticsearch7]* error occurs when the search engine is set to [!DNL OpenSearch]  in Adobe Commerce.
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# Terugvallen op [!DNL Elasticsearch7] wanneer zoekprogramma is ingesteld op [!DNL Opensearch]

Dit artikel verstrekt een oplossing voor de kwestie wanneer a *die terug naar[!DNL Elasticsearch7]* fout terugloopt voorkomt wanneer de onderzoeksmotor aan [!DNL OpenSearch] in Adobe Commerce wordt geplaatst.

## Betrokken versies

Adobe Commerce over cloudinfrastructuur 2.4.4 - 2.4.5

>[!NOTE]
>
>[!DNL OpenSearch] is beschikbaar als zoekprogramma vanaf Adobe Commerce 2.4.6.

## Probleem

U plaatst uw **onderzoeksmotor** aan **[!DNL OpenSearch]**, maar zie dit type van fout in het `var/log/support_report.log` dossier:

```[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []```

<u> Stappen om </u> te reproduceren:

1. Controleer of [!DNL OpenSearch] is geïnstalleerd door deze opdracht uit te voeren: `curl 127.0.0.1:9200`<br>
Als het *1.2.4* wijst, dan [!DNL OpenSearch] is reeds geïnstalleerd.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** .
1. Controleer het zoekprogramma. Deze wordt weergegeven [!DNL Elasticsearch7] .

## Oorzaak

Hoewel uw versie [!DNL OpenSearch] wel ondersteunt, herkent/accepteert de toepassing [!DNL Elasticsearch7] alleen als zoekengine.

Vanaf Adobe Commerce versie 2.4.6 is de toepassing bijgewerkt zodat [!DNL OpenSearch] als zoekprogramma kan worden geselecteerd.
Als u **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** in een niet wolkenmilieu gaat, zult u deze optie zoals aangetoond in de **Oplossing** hieronder kunnen veranderen.
(Opmerking: in een cloudomgeving kan dit veld niet worden gewijzigd omdat het zoekprogramma is vergrendeld in het `app/etc/env.php` -bestand.)

## Oplossing

Werk `SEARCH_CONFIGURATION` variabele in het `.magento.env.yaml` dossier bij, en zorg ervoor dat de **onderzoeksmotor** aan *[!DNL elasticsearch7]* wordt geplaatst.

## Gerelateerde lezing

[ de dienst van OpenSearch van de Opstelling ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) in Commerce op de gids van de Infrastructuur van de Wolk.
