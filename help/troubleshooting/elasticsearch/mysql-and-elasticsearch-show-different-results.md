---
title: MySQL en Elasticsearch geven verschillende resultaten weer
description: Dit artikel biedt een patch voor het bekende Adobe Commerce-probleem met cloudinfrastructuur 2.2.3 met betrekking tot het ophalen van verschillende zoekresultaten voor dezelfde zoekquery met MySQL en Elasticsearch.
exl-id: 37a0164a-0237-4200-ab9c-e0dbad7e2062
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MySQL en Elasticsearch geven verschillende resultaten weer

>[!WARNING]
>
> [De zoekfunctie voor MySQL-catalogus wordt verwijderd uit Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). U moet de Elasticsearch gastheer opstelling en gevormd hebben alvorens versie 2.4.0 te installeren. Zie [Elasticsearch installeren en configureren](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html) in onze ontwikkelaarsdocumentatie.

Dit artikel biedt een patch voor het bekende Adobe Commerce-probleem met cloudinfrastructuur 2.2.3 met betrekking tot het ophalen van verschillende zoekresultaten voor dezelfde zoekquery met MySQL en Elasticsearch.

## Probleem:

De zoekresultaten van de catalogus met dezelfde filterset verschillen afhankelijk van de zoekmachine die wordt gebruikt, MySQL of Elasticsearch.

<u>Stappen om te reproduceren</u> :

1. Installeer en configureer Elasticsearch.
1. Selecteer in de winkel een van de filters.
1. Noteer het aantal overeenkomende producten.
1. De standaardinstelling configureren [MySQL-zoekopdracht](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md).
1. Selecteer in de winkel een van de filters.
1. Noteer het aantal overeenkomende producten.

<u>Verwacht resultaat</u>: Het aantal overeenkomende producten is hetzelfde.

<u>Werkelijk resultaat</u>: Het aantal overeenkomende producten is anders.

## Reparatie

De patches zijn aan dit artikel gekoppeld. Als u een patch wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de gewenste bestandsnaam of klikt u op de volgende koppelingen:

[MDVA-12312\_EE\_2.2.3\_COMPOSER\_v1.patch downloaden](assets/MDVA-12312_EE_2.2.3_COMPOSER_v1.patch.zip)

[MDVA-14172\_EE\_2.2.6\_COMPOSER\_v1.patch downloaden](assets/MDVA-14172_EE_2.2.6_COMPOSER_v1.patch.zip)

### Compatibele Adobe Commerce-versies:

De patches zijn gemaakt voor:

* Adobe Commerce on cloud Infrastructure 2.2.3 (de `MDVA-12312_EE_2.2.3_COMPOSER_v1.patch` bestand)
* Adobe Commerce on cloud Infrastructure 2.2.6 (de `MDVA-14172_EE_2.2.6_COMPOSER_v1.patch` bestand)

De `MDVA-12312_EE_2.2.3_COMPOSER_v1.patch` patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce over wolkeninfrastructuur 2.2.4
* Adobe Commerce over wolkeninfrastructuur 2.2.5
* Adobe Commerce op locatie 2.2.3
* Adobe Commerce op locatie 2.2.4
* Adobe Commerce op locatie 2.2.5

De `MDVA-14172_EE_2.2.6_COMPOSER_v1.patch` patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce op locatie 2.2.6

## Hoe de pleister aanbrengen

Zie [Hoe een door Adobe geleverde componentpleister aanbrengen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze kennisbasis voor ondersteuning voor instructies.

## Bijgevoegde bestanden
