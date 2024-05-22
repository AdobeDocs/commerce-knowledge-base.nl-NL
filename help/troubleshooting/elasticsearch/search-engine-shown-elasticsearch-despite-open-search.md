---
title: '[!DNL Elasticsearch] wordt getoond als zoekmachine ondanks [!DNL OpenSearch] installatie'
description: Dit artikel biedt een oplossing voor de kwestie waar [!DNL Elasticsearch] wordt nog steeds weergegeven als zoekmachine voor Adobe Commerce in de cloud, zelfs na installatie of upgrade naar [!DNL OpenSearch].
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: 1f053f76ae56edc06bfe82e55210244c8ec4b8eb
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# [!DNL Elasticsearch] wordt getoond als zoekmachine ondanks [!DNL OpenSearch] installatie

Dit artikel biedt een oplossing voor de kwestie waar [!DNL Elasticsearch] wordt nog steeds weergegeven als zoekmachine voor Adobe Commerce in de cloud, zelfs na installatie of upgrade naar [!DNL OpenSearch].

## Betrokken versies

Adobe Commerce op cloud 2.4.3-p2 - 2.4.5-p6

>[!NOTE]
>
>[!DNL OpenSearch] is beschikbaar als zoekmachine vanaf Adobe Commerce 2.4.6.

## Probleem

[!DNL Elasticsearch] wordt nog steeds weergegeven als zoekmachine voor Adobe Commerce in de cloud, zelfs na installatie of upgrade naar [!DNL OpenSearch].

<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Controleer het zoekprogramma. Het wordt weergegeven [!DNL Elasticsearch7].

## Oorzaak

Adobe Commerce is hard-coded om te specificeren [!DNL Elasticsearch7] als zoekprogramma.

Dit mag niet worden verward met de geïnstalleerde versie van de service. De toepassing herkent alleen [!DNL Elasticsearch7] als zoekmachine, maar niet [!DNL OpenSearch], ook al wordt de onderliggende waarde gebruikt [!DNL OpenSearch] als de motor op de achtergrond.

## Oplossing

Om te verifiëren of [!DNL OpenSearch] is geïnstalleerd, voer het volgende bevel in werking:

**Methode 1**:

* Voer de volgende opdracht op de server uit: `curl 127.0.0.1:9200`. Het moet terugkeren [!DNL OpenSearch] met de versie.

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

* Gebruik het volgende bevel op Magento-wolk CLI: `magento-cloud relationships -p <project_id>`. Na het gebruiken van het bevel, bepaal [!DNL OpenSearch].

## Gerelateerde lezing

[OpenSearch-service instellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) in de handleiding Commerce on Cloud Infrastructure.
