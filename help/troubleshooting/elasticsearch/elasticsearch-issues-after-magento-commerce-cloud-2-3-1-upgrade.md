---
title: Problemen met Elasticsearch na upgrade naar Adobe Commerce Cloud Infrastructure 2.3.1+
description: In dit artikel wordt een oplossing besproken voor problemen tijdens de implementatie na de upgrade naar Adobe Commerce op versie 2.3.1+ van de cloudinfrastructuur, als u werkt met versie 2.x en 5.x van de Elasticsearch.
exl-id: 6ceeb2ea-528d-4c03-ab2b-c5aed46fd0a2
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Problemen met Elasticsearch na upgrade naar Adobe Commerce Cloud Infrastructure 2.3.1+

>[!WARNING]
>
>[ MySQL de motor van het catalogusonderzoek zal in Adobe Commerce 2.4.0 ](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md) worden verwijderd. U moet de Elasticsearch gastheeropstelling hebben en voorafgaand aan het installeren van versie 2.4.0 worden gevormd. Verwijs naar [ installeer en vorm Elasticsearch ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search).

>[!WARNING]
>
>Houd er rekening mee dat serviceupgrades niet naar de productieomgeving kunnen worden verplaatst zonder dat het infrastructuurteam hiervan 48 uur op de hoogte wordt gesteld. Dit is nodig omdat wij ervoor moeten zorgen dat wij een ingenieur van de infrastructuursteun beschikbaar hebben om uw configuratie binnen een gewenst tijdsbestek met minimale onderbreking aan uw productiemilieu bij te werken. Zo 48 uren voorafgaand aan wanneer uw veranderingen op productie moeten zijn [ een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voorleggen detailend uw vereiste de dienstverbetering en het verklaren van de tijd wanneer u het verbeteringsproces wilt beginnen.

In dit artikel wordt een oplossing besproken voor problemen tijdens de implementatie na de upgrade naar Adobe Commerce op versie 2.3.1+ van de cloudinfrastructuur, als u werkt met versie 2.x en 5.x van de Elasticsearch.

## Betrokken producten en versies:

* Adobe Commerce op cloudinfrastructuur 2.3.1+
* Elasticsearch 2.x en 5.x

## Oorzaak

Handelaren die een upgrade naar Adobe Commerce hebben uitgevoerd op een cloudinfrastructuur (versie 2.3.1 en hoger) en die een versie van Elasticsearch hebben die ouder is dan 6.x, kunnen fouten ondervinden bij de implementatie. Dit is omdat de versies 2.x en 5.x van de Elasticsearch [ Einde van het Leven ](https://www.elastic.co/support/eol) zijn en niet meer in Adobe Commerce gesteund. De client van de Elasticsearch moet up-to-date zijn of een implementatierisico lopen dat een fout veroorzaakt. Meer leren, verwijs naar [ Verandering de cliënt van de Elasticsearch ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search) in onze ontwikkelaarsdocumentatie.

## Probleem

Wanneer het opstellen van u ziet een foutenmelding gelijkend op het volgende, erop wijzend dat uw versie van de Elasticsearch niet compatibel is: *de dienstversie van de Elasticsearch 5.2.2 op infrastructuurlaag is niet compatibel met huidige versie van elasticsearch/elasticsearch module (6.7.0.0), die door uw toepassing van het Magento wordt gebruikt.* *U kunt deze kwestie bevestigen door de dienst van de Elasticsearch op uw infrastructuur van de Wolk van het Magento aan versie 6.x* te bevorderen. Andere symptomen van dit probleem zijn mogelijk ontbrekende afbeeldingen en problemen met filters in uw omgeving.

## Oplossing

>[!WARNING]
>
>Als u een gedeelde omgeving hebt, dient u ervoor te zorgen dat de installatie en de productie klaar zijn om te worden bijgewerkt.

Om dit probleem op te lossen, moeten de de cliëntmodule en dienst van de Elasticsearch van de Elasticsearch op de recentste geadviseerde versies zijn:

1. Volg de instructies om [ de module van de Elasticsearch ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search) in onze ontwikkelaarsdocumentatie te veranderen zodat hebt u de recentste geadviseerde versie van de de cliëntmodule van de Elasticsearch.
1. [ leg een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voor en verzoek een de dienstupdate van de Elasticsearch aan 6.x op het opvoeren en productie. Houd er rekening mee dat het enige tijd kan duren voordat een upgrade naar de service Elasticsearch is voltooid.

## Gerelateerde lezing

* [ Adobe Commerce 2.3 de vereisten van de technologiestapel ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/overview) in onze ontwikkelaarsdocumentatie.
* [ de dienst van de Elasticsearch van de opstelling ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch) in onze ontwikkelaarsdocumentatie.
* [ installeer en vorm Elasticsearch ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search) in onze ontwikkelaardocumentatie.
* [ verzeker Elasticsearch behoorlijk ](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) in onze basis van steunkennis wordt geïnstalleerd.
