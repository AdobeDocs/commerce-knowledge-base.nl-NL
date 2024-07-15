---
title: Problemen met de Recommendations-module Product in Adobe Commerce oplossen
description: In dit artikel worden suggesties voor het oplossen van problemen besproken voor de
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: b20ad74194bacb09116131f4a8da1006da75738a
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Problemen met de Recommendations-module Product in Adobe Commerce oplossen

In dit artikel worden suggesties voor het oplossen van problemen besproken voor de

```php
magento/product-recommendations
```

en de afhankelijkheid ervan

```php
saas-export
```

omdat u beide modules nodig hebt om het product Recommendations in Adobe Commerce te kunnen gebruiken.

## Betrokken producten en versies

* Adobe Commerce 2.4.4 - 2.4.7

## Probleemoplossing product-aanbevelingen module

Als u het

```php
magento/product-recommendations
```

de module correct (het Product van de Controle [ Recommendations - installeert en vormt Recommendations ](https://devdocs.magento.com/recommendations/install-configure.html) in onze ontwikkelaarsdocumentatie.), maar u ziet geen aanbevelingen, probeert het volgende:

* Het is mogelijk dat de module niet genoeg tijd heeft gehad om gedragsgegevens te verzamelen. Laat het systeem 24 uur werken, zodat het gegevens kan gaan verzamelen. Overweeg het opstellen van een aanbevelingstype dat geen gedragsgegevens, zoals &quot;meer als dit&quot;vereist.

* Als u niet de aanbevelingen ziet die u vormde, is het mogelijk er nog niet voldoende gegevens zijn om aanbevelingen voor de gebruiker te bouwen.

* Controleer of de SaaS-gegevensruimte of API-sleutel geldig is. Als u een fout na het specificeren van uw Ruimte van Gegevens SaaS of uw API sleutel tijdens de initialisering van productaanbevelingen krijgt, controleer om ervoor te zorgen u de [ Spatie van Gegevens SaaS en API sleutel ](https://docs.magento.com/user-guide/configuration/services/saas.html) (in onze gebruikersgids) correct bent ingegaan. Om ervoor te zorgen dat de MageID en de API-sleutel worden gekoppeld, moet de gebruiker die eigenaar is van de MageID, doorgaans de gebruiker die eigenaar is van de Adobe Commerce-licentie, dezelfde gebruiker zijn die de API-sleutel genereert. Als u MageID moet veranderen die werd gebruikt, [ een kaartje van de Steun ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voorleggen.

>[!NOTE]
>
>Als [ de Wijze van de Beperking van het Koekje ](https://docs.magento.com/m2/ce/user_guide/stores/compliance-cookie-restriction-mode.html) (in onze gebruikersgids) wordt toegelaten, verzamelt Adobe Commerce geen gedragsgegevens tot de verkooptoestemming. Als de modus Cookie-beperking is uitgeschakeld, verzamelt Adobe Commerce standaard gedragsgegevens.

## Export-module Catalog SaaS

Voor kwesties die verband houden met de Catalog SaaS-export (

```php
saas-export
```

) module:

1. Bevestig de [ bouwsteen ](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cron.html) (in onze ontwikkelaarsdocumentatie) banen lopen.
1. Bevestig de [ indexeerders ](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html) (in onze ontwikkelaarsdocumentatie) lopen en    ```php    Product Feed    ```    indexer is ingesteld op    ```php    Update by Schedule    ```    .
1. Bevestig dat de modules zijn ingeschakeld. De    ```php    saas-export    ```    metapack installeert de volgende modules, allen die moeten worden toegelaten:    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. Controleer de [ logboeken ](https://devdocs.magento.com/guides/v2.3/config-guide/cli/logging.html) (in onze ontwikkelaarsdocumentatie). Zorg ervoor dat er geen fouten aan de bovenstaande modules zijn gekoppeld.
1. Configuratiecache vernieuwen. Ga naar **Systeem** > **Hulpmiddelen** > **het Beheer van het Geheime voorgeheugen**, en ontruim het configuratiecache.
1. Bevestig dat er gegevens zijn in het dialoogvenster    ```php    catalog_data_exporter_products    ```    databasetabel.

## Gebeurtenissen

[ Gebeurtenissen van de Aanbeveling ](https://devdocs.magento.com/recommendations/verify.html), in onze ontwikkelaarsdocumentatie, beschrijft de gedragsgebeurtenissen die naar Adobe Commerce worden verzonden.

## Gerelateerde lezing

* [ Product Recommendations - Overzicht ](https://devdocs.magento.com/recommendations/product-recs.html) in onze ontwikkelaarsdocumentatie
* [ Product Recommendations - installeer en vorm Recommendations ](https://devdocs.magento.com/recommendations/install-configure.html) in onze ontwikkelaarsdocumentatie
* [ Marketing - het Product Recommendations ](https://docs.magento.com/m2/ee/user_guide/marketing/product-recommendations.html) in onze gebruikersgids
* [ creeer Product Recommendations ](https://docs.magento.com/m2/ee/user_guide/marketing/create-new-rec.html) in onze gebruikersgids
