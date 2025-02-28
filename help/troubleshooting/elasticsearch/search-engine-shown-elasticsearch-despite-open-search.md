---
title: '[!DNL Elasticsearch] wordt getoond als onderzoeksmotor ondanks  [!DNL OpenSearch]  installatie'
description: Dit artikel verstrekt een oplossing voor de kwestie waar  [!DNL Elasticsearch]  nog als onderzoeksmotor voor Adobe Commerce op wolk na het installeren of het bevorderen aan  [!DNL OpenSearch] wordt getoond.
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: b3f68e43ce3c4fdea001db1d8ba2774900db7dba
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# [!DNL Elasticsearch] wordt weergegeven als zoekprogramma ondanks [!DNL OpenSearch] installatie

Dit artikel biedt een oplossing voor het probleem waarbij [!DNL Elasticsearch] nog steeds wordt weergegeven als zoekengine voor Adobe Commerce in de cloud, zelfs na installatie of upgrade naar [!DNL OpenSearch] .

## Betrokken versies

Adobe Commerce op cloud 2.4.4 - 2.4.5-p11

>[!NOTE]
>
>[!DNL OpenSearch] is beschikbaar als zoekprogramma vanaf Adobe Commerce 2.4.6.

## Probleem

[!DNL Elasticsearch] wordt nog steeds weergegeven als de zoekengine voor Adobe Commerce in de cloud, zelfs na installatie of upgrade naar [!DNL OpenSearch] .

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** .
1. Controleer het zoekprogramma. Deze wordt weergegeven [!DNL Elasticsearch7] .

## Oorzaak

[!DNL Elasticsearch7] is in Adobe Commerce gecodeerd als zoekprogramma dat in deze versies wordt gebruikt.

Dit mag niet worden verward met de geïnstalleerde versie van de service. Hoewel er geen [!DNL Opensearch] -module in de code is opgenomen, kan Adobe Commerce gebruikmaken van de onderliggende [!DNL Opensearch] -service.

## Oplossing

Voer de volgende opdracht uit om te controleren of [!DNL OpenSearch] is geïnstalleerd:

**Methode 1**:

* Voer de volgende opdracht uit op de server: `curl 127.0.0.1:9200` . Deze moet [!DNL OpenSearch] retourneren met de versie ervan.

Voorbeeld:

```
$ curl 127.0.0.1:9200
{
  "name" : $clusterName,
  "cluster_name" : "opensearch_stg",
  "cluster_uuid" : $clusterUuid,
  "version" : {
    "distribution" : "opensearch",
    "number" : "1.2.4",
    "build_type" : "deb",
    "build_hash" : "44ccdbaed5fe5a8b02d99a611857a671b6dd909d",
    "build_date" : "2022-11-08T09:23:45.993372Z",
    "build_snapshot" : false,
    "lucene_version" : "8.10.1",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "The OpenSearch Project: https://opensearch.org/"
}
```

**Methode 2**:

* Gebruik de volgende opdracht op de CLI Magento-cloud: `magento-cloud relationships -p <project_id>`. Zoek [!DNL OpenSearch] nadat u de opdracht hebt gebruikt.

## Gerelateerde lezing

[ de dienst van OpenSearch van de Opstelling ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) in Commerce op de gids van de Infrastructuur van de Wolk.
