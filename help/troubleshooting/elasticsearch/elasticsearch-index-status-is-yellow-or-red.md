---
title: De indexstatus van de Elasticsearch is 'geel' of 'rood'
description: Het artikel bevat een oplossing voor het geval de indexstatus van de Elasticsearch niet '*green*' is. '*yellow*' geeft de waarde normal aan en '*red*' geeft de waarde bad aan. De status 'geel' of 'rood' kan voorkomen in combinatie met ontbrekende producten of de weergave van oude productinformatie.
exl-id: 27689511-6a41-41a9-8dda-a627d2f65263
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# De indexstatus van de Elasticsearch is &#39;geel&#39; of &#39;rood&#39;

>[!WARNING]
>
> [ MySQL de motor van het catalogusonderzoek zal in Adobe Commerce 2.4.0 ](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md) worden verwijderd. U moet de Elasticsearch gastheeropstelling hebben en voorafgaand aan het installeren van versie 2.4.0 worden gevormd. Verwijs naar [ installeer en vorm Elasticsearch ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search).

Het artikel verstrekt een moeilijke situatie voor wanneer de Status van de Index van de Elasticsearch niet &quot;*groen*&quot;is. &quot;*geel*&quot;wijst op normaal, en &quot;*rood*&quot;wijst op slecht. De status &#39;geel&#39; of &#39;rood&#39; kan voorkomen in combinatie met ontbrekende producten of de weergave van oude productinformatie.

## Betrokken versies en producten

* Adobe Commerce op cloud-infrastructuur 2.2.x, 2.3.x
* Adobe Commerce op locatie 2.2.x, 2.3.x

## Probleem

De index van het de catalogusonderzoek van de Elasticsearch is langzaam, resulterend in een status van &quot;*geel*&quot;of &quot;*rood*&quot;eerder dan &quot;*groen*&quot;. Het is ook mogelijk dat er ontbrekende wijzigingen aan de voorkant optreden.

## Oorzaak

Er kunnen verschillende mogelijke oorzaken zijn. Eén oorzaak is dat er onvoldoende schijfruimte beschikbaar is voor de Elasticsearch-instantie. Een andere oorzaak zijn dubbele indices.

## Oplossing

Creeer een nieuwe mysql stortplaats alvorens deze stappen te volgen en hen buiten kantooruren uit te voeren om potentieel het beïnvloeden van uw cliënten te vermijden:

1. Schakel tijdelijk over naar MySQL-zoekopdracht - schakel MySQL-zoekopdracht in. (Opmerking: vergeet niet terug te gaan naar de Elasticsearch of ondervindt mogelijk prestatieproblemen).
1. Als u gedupliceerde indexen wilt identificeren, voert u de volgende opdracht uit:

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

1. Indexen verwijderen:

   ```
   curl -XDELETE localhost:9200/[your_index_name_here]
   ```

1. Herstelbare Elasticsearch.
1. Voer de volledige re-index uit.
1. Controleer de status van indexen door de volgende opdracht uit te voeren:

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

Als deze stappen niet werken, [ een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voorleggen.

## Gerelateerde lezing

Meer leren, verwijs naar [ gezondheid API van de Cluster van de Elasticsearch ](https://www.elastic.co/guide/en/elasticsearch/reference/current/cluster-health.html).
