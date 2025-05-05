---
title: Standaardwaarden voor thema's herstellen
description: Afhankelijk van de problemen die u tegenkomt bij het aanpassen van uw thema's en het ontwikkelen van uw winkel, hebt u mogelijk geen toegang via de Commerce Admin. U kunt het standaardthema wissen en herstellen zonder de beheerdersfunctie te gebruiken. Nadat u het thema hebt gewist, wordt het standaardthema Luminantie toegepast.
exl-id: 86304dd5-f448-4dcc-ad07-04ecc6c85b6d
feature: Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Standaardwaarden voor thema&#39;s herstellen

Afhankelijk van de problemen die u tegenkomt bij het aanpassen van uw thema&#39;s en het ontwikkelen van uw winkel, hebt u mogelijk geen toegang via de Commerce Admin. U kunt het standaardthema wissen en herstellen zonder de beheerdersfunctie te gebruiken. Nadat u het thema hebt gewist, wordt het standaardthema Luminantie toegepast.

Tijdens de ontwikkeling van Adobe Commerce (alle implementaties) en Magento Open Source-onderdelen (modules, thema&#39;s en taalpakketten), vereist uw snel veranderende omgeving dat u regelmatig bepaalde mappen en cache wist. Anders wordt de code uitgevoerd met uitzonderingen en werkt deze niet correct. Voor details, zie [ Duidelijke folders tijdens ontwikkeling ](https://developer.adobe.com/commerce/php/development/components/clear-directories/) in onze ontwikkelaarsdocumentatie.

## Milieu en technologieën

* Adobe Commerce ter plaatse
* Adobe Commerce over cloudinfrastructuur
* Magento Open Source

## Vereisten

* Database-gereedschappen

## Stappen

Als u het winkelthema opnieuw moet instellen, maar geen toegang hebt tot het deelvenster Beheer, kunt u het als volgt opnieuw instellen in de database:

1. Gebruik een gegevensbestandhulpmiddel zoals [ phpMyAdmin ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin) of toegang manueel OB van de bevellijn om de volgende SQL vraag uit te voeren: `UPDATE core_config_data SET value=NULL WHERE path='design/theme/theme_id'`
1. Wis de volgende directory&#39;s:
   * `pub/static/frontend`
   * `var/view_preprocessing`
   * `var/cache`
   * `var/page_cache`

Op deze manier wordt er geen thema ingesteld op het weergaveniveau van de winkel. Wanneer u de voorpagina&#39;s van de winkel opnieuw laadt, wordt het standaardthema Luminantie toegepast.

## Aanvullende informatie

* [ Duidelijke folders tijdens ontwikkeling ](https://developer.adobe.com/commerce/php/development/components/clear-directories/) in onze ontwikkelingsdocumentatie
