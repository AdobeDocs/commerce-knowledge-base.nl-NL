---
title: Problemen met de module [!UICONTROL Product Recommendations] in Adobe Commerce oplossen
description: In dit artikel wordt ingegaan op suggesties voor het oplossen van problemen voor de module [!UICONTROL Product Recommendations] in Adobe Commerce.
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# Problemen met de module [!UICONTROL Product Recommendations] in Adobe Commerce oplossen

In dit artikel worden suggesties voor het oplossen van problemen besproken voor de

```php
magento/product-recommendations
```

en de afhankelijkheid ervan

```php
saas-export
```

aangezien u beide modules nodig hebt om het [!UICONTROL Product Recommendations] hulpmiddel in Adobe Commerce te gebruiken.

## Betrokken producten en versies

* Adobe Commerce 2.4.4 - 2.4.7

## Probleemoplossing product-aanbevelingen module

Als u het

```php
magento/product-recommendations
```

correct, (Controle [[!UICONTROL Product Recommendations - Install and Configure] ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure) in onze ontwikkelaarsdocumentatie.) maar u ziet geen aanbevelingen, probeer het volgende:

* Het is mogelijk dat de module niet genoeg tijd heeft gehad om gedragsgegevens te verzamelen. Laat het systeem 24 uur werken, zodat het gegevens kan gaan verzamelen. Overweeg het opstellen van een aanbevelingstype dat geen gedragsgegevens, zoals &quot;*meer als dit*&quot;vereist.

* Als u niet de aanbevelingen ziet die u vormde, is het mogelijk er nog niet voldoende gegevens zijn om aanbevelingen voor de gebruiker te bouwen.

* Controleer of de [!DNL SaaS] Data Space of [!DNL API] Key geldig is. Als u een fout na het specificeren van uw [!DNL SaaS] Ruimte van Gegevens of uw [!DNL API] sleutel tijdens de initialisering van productaanbevelingen krijgt, controle om ervoor te zorgen u de [[!DNL SaaS]  Ruimte van Gegevens en  [!DNL API]  sleutel ](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) (in onze gebruikersgids) correct bent ingegaan. Om ervoor te zorgen dat de [!DNL MageID] - en [!DNL API] -toets worden gekoppeld, moet de gebruiker die eigenaar is van de [!DNL MageID] -toets, doorgaans de gebruiker die eigenaar is van de Adobe Commerce-licentie, dezelfde gebruiker zijn die de [!DNL API] -toets genereert. Als u [!DNL MageID] moet veranderen dat werd gebruikt, [ een kaartje van de Steun ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voorleggen.

>[!NOTE]
>
>Als [**[!UICONTROL Cookie Restriction Mode]**](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law) (in onze gebruikersgids) **&#x200B; wordt toegelaten, verzamelt Adobe Commerce geen gedragsgegevens tot de winkelinstemming. Als &#x200B;** [!UICONTROL Cookie Restriction Mode]&#x200B;**&#x200B;** gehandicapt is, verzamelt Adobe Commerce gedragsgegevens door gebrek.

## Catalogus [!DNL SaaS] Exportmodule

Voor problemen met betrekking tot de catalogus [!DNL SaaS] Exporteren (

```php
saas-export
```

) module:

1. Bevestig [[!DNL cron] ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) (in onze ontwikkelaarsdocumentatie) banen loopt.
1. Bevestig [[!UICONTROL indexers] ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers) (in onze ontwikkelaarsdocumentatie) loopt en    ```php    Product Feed    ```    [!UICONTROL indexer] is ingesteld op    ```php    Update by Schedule    ```    .
1. Bevestig de modules *worden toegelaten*. De    ```php    saas-export    ```    De metapackage installeert de volgende modules, allen die *moeten worden toegelaten*:    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. Controleer de [ logboeken ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/enable-logging) (in onze ontwikkelaarsdocumentatie). Zorg ervoor dat er geen fouten aan de bovenstaande modules zijn gekoppeld.
1. Vernieuw de [!UICONTROL Configuration cache]. Ga naar **Systeem** > **Hulpmiddelen** > **het Beheer van het Geheime voorgeheugen**, en ontruim [!UICONTROL Configuration cache].
1. Controleer of de databasetabel `cde_products_products_feed` gegevens bevat.

   >[!NOTE]
   >
   >Controleer de tabel `catalog_data_exporter_products` als u die tabel niet kunt vinden. De tabelnaam is gewijzigd in [!DNL Data Export] versie 103.3.0.

## Gebeurtenissen

[ verifieer de Inzameling van de Gebeurtenis ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/verify), in onze ontwikkelaarsdocumentatie, beschrijft de gedragsgebeurtenissen die naar Adobe Commerce worden verzonden.

## Gerelateerde lezing

* [ Ontwikkeling van de Beheerder van Recommendations van het Product ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/development-overview) in onze ontwikkelingsdocumentatie
* [ Inleiding aan Product Recommendations ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview) in de Gids van Recommendations van het Product
* [ creeer Product Recommendations ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/admin/create) in de Gids van Recommendations van het Product
* [ Logboeken van het Overzicht en los ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging) in de [!DNL SaaS] Gids van de Uitvoer van Gegevens problemen op
* [[!DNL SaaS]  de Nota&#39;s van de Versie van de Uitbreiding van de Gegevens van de Uitvoer van Gegevens ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes) in de Gids van de Uitvoer van Gegevens van Adobe Commerce voor [!DNL SaaS] de Diensten
* [ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce

