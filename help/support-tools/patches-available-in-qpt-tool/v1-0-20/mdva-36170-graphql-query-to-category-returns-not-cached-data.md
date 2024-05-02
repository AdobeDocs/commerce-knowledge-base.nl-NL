---
title: 'MDVA-36170: GraphQL query to category returns not cached data'
description: De patch MDVA-36170 verhelpt het probleem waarbij het resultaat van de GraphQL-query niet in de cache wordt opgeslagen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 is geïnstalleerd. De patch-id is MDVA-36170. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: 6249b751-4b71-4833-ab86-ded615d648a8
feature: Cache, GraphQL, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# MDVA-36170: GraphQL query to category returns not cached data

De patch MDVA-36170 verhelpt het probleem waarbij het resultaat van de GraphQL-query niet in de cache wordt opgeslagen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 is geïnstalleerd. De patch-id is MDVA-36170. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.3.6

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.1 - 2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Hiermee wordt het probleem verholpen waarbij het resultaat van de GraphQL-query niet in de cache wordt opgeslagen.

<u>Stappen om te reproduceren</u>:

De handelaar gebruikt de methode van de GET voor GraphQL caching maar krijgt niet de caching gegevens.

<pre>https://magento_url/graphql?query={ products(filter: {category_id: {eq: "2"}, pageSize: 2000, currentPage: 1, sort: {position: ASC}) { items { sku id name { html } url_key details image { label gallery_url } _typename quantity_in small_image { gallery_url label } product_price_range { maximum_range price { final_price { value } } minimum_price { final_price { value } } } } ... on ConfigurableProduct { variants{ code label value_index } product{ sku quantity_in } } } } } } } }}</pre>

<u>Verwachte resultaten</u>:

De gegevens worden in de cache opgeslagen.

<u>Werkelijke resultaten</u>:

De gegevens worden niet in de cache opgeslagen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
