---
title: "MDVA-31791 patch: improve for product page with related products and target rules"
description: De MDVA-31791-patch verbetert de prestaties van productpagina's wanneer [Verwante producten](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) of [Verwante productregels](https://docs.magento.com/user-guide/marketing/product-related-rules.html) (doelregels) worden gebruikt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.1.
exl-id: e737bccb-d9eb-4794-9d6b-2c22fa8edaa2
feature: Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# MDVA-31791 patch: improve for product page with related products and target rules

De MDVA-31791-patch verbetert de prestaties van productpagina&#39;s wanneer [Verwante producten](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) of [Regels voor verwante producten](https://docs.magento.com/user-guide/marketing/product-related-rules.html) (doelregels) worden gebruikt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.1.

## Betrokken producten en versies

**De patch is gemaakt voor de Adobe Commerce-versie:**

Adobe Commerce over cloudinfrastructuur 2.4.0

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.4, 2.3.4-p1, 2.3.4-p2, 2.4.0, 2.4.0-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Lage prestaties van productpagina&#39;s als Verwante producten of de regels van het Doel worden gebruikt.

Overweeg de MDVA-31791 pleister toe te passen als u de pleister gaat gebruiken [Verwante producten](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) of [Verwante productregels](https://docs.magento.com/user-guide/marketing/product-related-rules.html) functionaliteit.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
