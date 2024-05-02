---
title: Terugvallen op [!DNL Elasticsearch7] als zoekprogramma is ingesteld op [!DNL Opensearch]
description: Dit artikel biedt een oplossing voor het probleem wanneer een *Falling terug naar [!DNL Elasticsearch7]* error occurs when the search engine is set to [!DNL OpenSearch] in Adobe Commerce.
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# Terugvallen op [!DNL Elasticsearch7] als zoekprogramma is ingesteld op [!DNL Opensearch]

Dit artikel biedt een oplossing voor het probleem wanneer een *Terugvallen op[!DNL Elasticsearch7]* Er treedt een fout op wanneer de zoekfunctie is ingesteld op [!DNL OpenSearch] in Adobe Commerce.

## Betrokken versies

Adobe Commerce over cloudinfrastructuur 2.4.4 - 2.4.5

>[!NOTE]
>
>[!DNL OpenSearch] is beschikbaar als zoekmachine vanaf Adobe Commerce 2.4.6.

## Probleem

U stelt uw **zoekmachine** tot **[!DNL OpenSearch]**, maar raadpleeg dit type fout in het dialoogvenster `var/log/support_report.log` bestand:

```[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []```

<u>Stappen om te reproduceren</u>:

1. Controleren of [!DNL OpenSearch] is geïnstalleerd door deze opdracht uit te voeren: `curl 127.0.0.1:9200`<br>
Als dit aangeeft *1.2.4.* vervolgens [!DNL OpenSearch] is al geïnstalleerd.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Controleer het zoekprogramma. Het wordt weergegeven [!DNL Elasticsearch7].

## Oorzaak

Ook al wordt uw versie wel ondersteund [!DNL OpenSearch]wordt de toepassing alleen herkend/geaccepteerd [!DNL Elasticsearch7] als zoekprogramma.

Vanaf Adobe Commerce versie 2.4.6 is de toepassing bijgewerkt op [!DNL OpenSearch] te selecteren als zoekprogramma.
Als u gaat naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** in een niet-cloud-omgeving kunt u deze optie wijzigen, zoals wordt weergegeven in het dialoogvenster **Oplossing** hieronder.
(Opmerking: in een cloudomgeving kan dit veld niet worden gewijzigd omdat het zoekprogramma is vergrendeld in het dialoogvenster `app/etc/env.php` bestand.)

## Oplossing

Werk de `SEARCH_CONFIGURATION` in de `.magento.env.yaml` en zorgt ervoor dat de **zoekmachine** is ingesteld op *[!DNL elasticsearch7]*.

## Gerelateerde lezing

[OpenSearch-service instellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) in de handleiding Commerce on Cloud Infrastructure.
