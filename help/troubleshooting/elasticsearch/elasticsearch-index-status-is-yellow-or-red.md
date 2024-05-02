---
title: De indexstatus van de Elasticsearch is 'geel' of 'rood'
description: Het artikel bevat een oplossing voor het geval de indexstatus van de Elasticsearch niet '*green*' is. '*yellow*' geeft de waarde normal aan en '*red*' geeft de waarde bad aan. De status 'geel' of 'rood' kan voorkomen in combinatie met ontbrekende producten of de weergave van oude productinformatie.
exl-id: 27689511-6a41-41a9-8dda-a627d2f65263
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# De indexstatus van de Elasticsearch is &#39;geel&#39; of &#39;rood&#39;

>[!WARNING]
>
> [De zoekfunctie voor MySQL-catalogus wordt verwijderd uit Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). U moet de Elasticsearch gastheeropstelling hebben en voorafgaand aan het installeren van versie 2.4.0 worden gevormd. Zie [Elasticsearch installeren en configureren](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html).

Het artikel bevat een oplossing voor het geval de indexstatus van de Elasticsearch niet &#39;*groen*&quot;. &#39;*geel*&#39; geeft normaal aan, en &#39;*rood*&#39; geeft aan dat het slecht is. De status &#39;geel&#39; of &#39;rood&#39; kan voorkomen in combinatie met ontbrekende producten of de weergave van oude productinformatie.

## Betrokken versies en producten

* Adobe Commerce op cloud-infrastructuur 2.2.x, 2.3.x
* Adobe Commerce op locatie 2.2.x, 2.3.x

## Probleem

De zoekindex van de Elasticsearch-catalogus is traag, wat resulteert in de status &#39;*geel*&#39; of &#39;*rood*&#39; in plaats van &#39;*groen*&quot;. Het is ook mogelijk dat er ontbrekende wijzigingen aan de voorkant optreden.

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

Als deze stappen niet werken, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Gerelateerde lezing

Raadpleeg voor meer informatie [Elasticsearch Cluster Health API](https://www.elastic.co/guide/en/elasticsearch/reference/current/cluster-health.html).
