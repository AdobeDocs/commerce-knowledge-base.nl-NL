---
title: 'ACSD-55100: [!DNL GraphQL]  keert geen producten voorbij 10k in onderzoeksresultaten terug'
description: Pas de ACSD-55100-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de GraphQL in de zoekresultaten geen producten retourneert die hoger zijn dan *10k*.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 951e5cd4-9690-43df-9e51-deab73f9eb54
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# ACSD-55100: [!DNL GraphQL] retourneert geen producten van meer dan 10 kB in zoekresultaten

ACSD-55100 herstelt de flard waar [!DNL GraphQL] geen producten voorbij *10k* in de onderzoeksresultaten terugkeert. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 wordt geïnstalleerd. De patch-id is ACSD-55100. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!DNL GraphQL] keert geen producten voorbij *10k* in de onderzoeksresultaten terug.

<u> Eerste vereisten </u>:

Gebruik in het geval van **[!DNL OpenSearch]** de nieuwste beschikbare versie.

Om het gerapporteerde probleem op te lossen, wordt de functie Punt in tijd geïntroduceerd, die beschikbaar is na **[!DNL OpenSearch]** 2.5.0 en versie 2.2 van het `opensearch-project/opensearch-php` -pakket vereist.

Er is echter een conflict met de `magento/magento-cloud-metapackage` , die een afhankelijkheid van het `opensearch-project/opensearch-php` -pakket opgeeft dat lager moet zijn dan versie 2.0.1.


Dit gebiedsdeel verhindert het bijwerken van [ openssearch-project/openssearch-php ] pakket aan recentste versie 2.2.

Dientengevolge, ontmoet het systeem de volgende fout en keert ongeldige resultaten voor producten terug die *10.000* overschrijden.

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

De bestaande afhankelijkheid maakt het lastig om rechtstreeks een versie toe te voegen aan het `composer.json` -bestand en het `opensearch-project/opensearch-php` -pakket bij te werken naar versie 2.2.

Neem de volgende regel op in het `composer.json` -hoofdbestand onder het verplichte blok om het probleem op te lossen. Hierna kunt u het pakket opnieuw implementeren om het probleem bij te werken naar de nieuwste versie.

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u> Stappen om </u> te reproduceren:

1. Produceer de catalogus met *15k* producten.
1. Verstuur de [!DNL GraphQL]:

```
    query {
    products(
    filter: {
    # category_id:{eq:""}
    }
    , pageSize: 5, currentPage: 1

    ) {
    total_count
    page_info {
    current_page
    page_size
    total_pages
     }

     aggregations {

    attribute_code
    count
    label
    options {
    label
    value

    }
    }

    items {
    uid
    sku
    is_for_clearance
    categories {
    name
    breadcrumbs {
    category_name
    category_uid
    }
    display_mode
    description
    }
    }
    }
    }
```

<u> Verwachte resultaten </u>:

Total_count = *15k*
U zou alle producten moeten kunnen tonen.

<u> Ware resultaten </u>:

Total_count = *10k*
U kunt geen meer producten krijgen om na de *10k* partij te tonen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
