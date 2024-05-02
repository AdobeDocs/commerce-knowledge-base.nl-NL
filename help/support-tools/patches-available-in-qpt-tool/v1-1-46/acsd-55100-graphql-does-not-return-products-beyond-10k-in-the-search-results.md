---
title: "ACSD-55100 [!DNL GraphQL] retourneert geen producten van meer dan 10 kB in zoekresultaten"
description: Pas de ACSD-55100-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de GraphQL in de zoekresultaten geen producten retourneert die hoger zijn dan *10k*.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 951e5cd4-9690-43df-9e51-deab73f9eb54
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# ACSD-55100: [!DNL GraphQL] retourneert geen producten van meer dan 10 k in zoekresultaten

De ACSD-55100-patch verhelpt het probleem waarbij [!DNL GraphQL] retourneert geen andere producten dan *10 kB* in de zoekresultaten. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 is geïnstalleerd. De patch-id is ACSD-55100. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!DNL GraphQL] retourneert geen andere producten dan *10 kB* in de zoekresultaten.

<u>Vereisten</u>:

In geval van **[!DNL OpenSearch]**, zorgt u ervoor dat u de nieuwste beschikbare versie gebruikt.

Om het gemelde probleem op te lossen, wordt de functie Punt in tijd geïntroduceerd, die beschikbaar is na **[!DNL OpenSearch]** 2.5.0 en vereist versie 2.2 van het `opensearch-project/opensearch-php` pakket.

Er is echter een conflict met de `magento/magento-cloud-metapackage`, die een afhankelijkheid van de `opensearch-project/opensearch-php` pakket dat lager moet zijn dan versie 2.0.1.


Deze afhankelijkheid voorkomt het bijwerken van de [openssearch-project/openssearch-php] naar de recentste versie 2.2.

Dientengevolge, ontmoet het systeem de volgende fout en keert ongeldige resultaten voor producten die overschrijden *10 000*.

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

Het bestaande gebiedsdeel maakt het uitdagend om een versie aan de `composer.json` bestand en werk de `opensearch-project/opensearch-php` naar versie 2.2.

Neem de volgende regel op in uw hoofd om het probleem op te lossen `composer.json` bestand onder het verplichte blok. Hierna kunt u het pakket opnieuw implementeren om het probleem bij te werken naar de nieuwste versie.

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>Stappen om te reproduceren</u>:

1. De catalogus genereren met *15 duodecies* producten.
1. Verzend de [!DNL GraphQL]:

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

<u>Verwachte resultaten</u>:

Total_count = *15 duodecies*
U zou alle producten moeten kunnen tonen.

<u>Werkelijke resultaten</u>:

Total_count = *10 kB*
U kunt geen producten meer laten zien na de *10 kB* batch.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
