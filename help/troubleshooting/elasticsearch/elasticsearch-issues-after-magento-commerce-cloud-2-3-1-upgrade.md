---
title: Problemen met Elasticsearch na upgrade naar Adobe Commerce Cloud Infrastructure 2.3.1+
description: In dit artikel wordt een oplossing besproken voor problemen tijdens de implementatie na de upgrade naar Adobe Commerce op versie 2.3.1+ van de cloudinfrastructuur, als u werkt met versie 2.x en 5.x van de Elasticsearch.
exl-id: 6ceeb2ea-528d-4c03-ab2b-c5aed46fd0a2
feature: Cloud
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Problemen met Elasticsearch na upgrade naar Adobe Commerce Cloud Infrastructure 2.3.1+

>[!WARNING]
>
>[De zoekfunctie voor MySQL-catalogus wordt verwijderd uit Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). U moet de Elasticsearch gastheeropstelling hebben en voorafgaand aan het installeren van versie 2.4.0 worden gevormd. Zie [Elasticsearch installeren en configureren](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html).

>[!WARNING]
>
>Houd er rekening mee dat serviceupgrades niet naar de productieomgeving kunnen worden verplaatst zonder dat het infrastructuurteam hiervan 48 uur op de hoogte wordt gesteld. Dit is nodig omdat wij ervoor moeten zorgen dat wij een ingenieur van de infrastructuursteun beschikbaar hebben om uw configuratie binnen een gewenst tijdsbestek met minimale onderbreking aan uw productiemilieu bij te werken. Dus 48 uur voor het moment dat uw veranderingen in productie moeten zijn [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) het gedetailleerd van uw vereiste de dienstverbetering en het verklaren van de tijd wanneer u het verbeteringsproces wilt beginnen.

In dit artikel wordt een oplossing besproken voor problemen tijdens de implementatie na de upgrade naar Adobe Commerce op versie 2.3.1+ van de cloudinfrastructuur, als u werkt met versie 2.x en 5.x van de Elasticsearch.

## Betrokken producten en versies:

* Adobe Commerce op cloudinfrastructuur 2.3.1+
* Elasticsearch 2.x en 5.x

## Oorzaak

Handelaren die een upgrade naar Adobe Commerce hebben uitgevoerd op een cloudinfrastructuur (versie 2.3.1 en hoger) en die een versie van Elasticsearch hebben die ouder is dan 6.x, kunnen fouten ondervinden bij de implementatie. Dit komt omdat Elasticsearch versies 2.x en 5.x [Einde van levensduur](https://www.elastic.co/support/eol) en worden niet meer ondersteund in Adobe Commerce. De client van de Elasticsearch moet up-to-date zijn of een implementatierisico lopen dat een fout veroorzaakt. Raadpleeg voor meer informatie [De Elasticsearch-client wijzigen](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html) in onze ontwikkelaarsdocumentatie.

## Probleem

Wanneer het opstellen ziet u een foutenmelding gelijkend op het volgende, erop wijzend dat uw versie van de Elasticsearch niet compatibel is: *Versie 5.2.2 van de de dienstdienst van de Elasticsearch op infrastructuurlaag is niet compatibel met huidige versie van elasticsearch/elasticsearch module (6.7.0.0), die door uw toepassing van het Magento wordt gebruikt.*  *U kunt dit probleem verhelpen door de service Elasticsearch op uw Magento Cloud-infrastructuur te upgraden naar versie 6.x*. Andere symptomen van dit probleem zijn mogelijk ontbrekende afbeeldingen en problemen met filters in uw omgeving.

## Oplossing

>[!WARNING]
>
>Als u een gedeelde omgeving hebt, dient u ervoor te zorgen dat de installatie en de productie klaar zijn om te worden bijgewerkt.

Om dit probleem op te lossen, moeten de de cliëntmodule en dienst van de Elasticsearch van de Elasticsearch op de recentste geadviseerde versies zijn:

1. Volg de instructies op [de module Elasticsearch wijzigen](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html) in onze ontwikkelaarsdocumentatie zodat hebt u de recentste geadviseerde versie van de cliëntmodule van de Elasticsearch.
1. [Een ondersteuningsticket verzenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) en een update van de de dienstdienst van de Elasticsearch aan 6.x op het opvoeren en productie vragen. Houd er rekening mee dat het enige tijd kan duren voordat een upgrade naar de service Elasticsearch is voltooid.

## Gerelateerde lezing

* [Adobe Commerce 2.3-technologie stapelvereisten](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements-tech.html) in onze ontwikkelaarsdocumentatie.
* [Service Elasticsearch instellen](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html) in onze ontwikkelaarsdocumentatie.
* [Elasticsearch installeren en configureren](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html) in onze ontwikkelaarsdocumentatie.
* [Controleer of de Elasticsearch correct is geïnstalleerd](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) in onze kennisbasis voor ondersteuning.
