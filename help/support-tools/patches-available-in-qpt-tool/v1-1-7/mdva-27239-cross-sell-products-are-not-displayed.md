---
title: "MDVA-27239: Cross-sell products are not displayed"
description: De MDVA-27239-patch verhelpt het probleem waarbij cross-sell-producten niet worden weergegeven. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.3.6.
exl-id: a0392a07-645d-4811-8547-2c67e20b6313
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-27239: Kruisverkoop wordt niet weergegeven

De MDVA-27239-patch verhelpt het probleem waarbij cross-sell-producten niet worden weergegeven. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.3.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.3.4, 2.4.0

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.3.5-p2, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Kruisverkoop-producten worden niet weergegeven in het cross-sellblok op de winkelwagentje.

<u>Vereisten</u>:

1. Schakel de module Magento_TargetRule uit of verwijder deze uit het lay-outblok Magento\TargetRule\Block\Checkout\Cart\Crosssell.
1. Product 1 maken.
1. Creeer een planningsupdate voor Product 1, zodat zullen de nieuwe producten row_id verschillend van entity_id hebben.
1. Maak product 2, product 3 en product 4.
1. Stel Product 3 in als cross-sell voor Product 4.
1. Stel Product 4 in als cross-sell voor Product 2.

<u>Stappen om te reproduceren</u>:

1. Voeg product 4 en product 2 toe aan het winkelwagentje.
1. Controleer de winkelwagenpagina.

<u>Verwachte resultaten</u>:

Product 3 wordt weergegeven in een blok voor meerdere verkooppunten.

<u>Werkelijke resultaten</u>:

Kruisverkoop is leeg.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
