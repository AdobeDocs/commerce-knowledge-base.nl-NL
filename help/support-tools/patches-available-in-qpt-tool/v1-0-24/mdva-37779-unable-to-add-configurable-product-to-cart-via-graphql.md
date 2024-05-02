---
title: 'MDVA-37779: Kan configureerbaar product niet toevoegen aan winkelwagentje via GraphQL'
description: De MDVA-37779 Adobe Commerce-patch lost het probleem op waarbij het onmogelijk is om een configureerbaar product aan winkelwagentje toe te voegen wanneer de website-id niet gelijk is aan de winkel-id. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 is geïnstalleerd. De patch-id is MDVA-3779. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4. 
exl-id: 5f344896-39c3-4e17-89b8-1b987bae2968
feature: GraphQL, Configuration, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# MDVA-37779: Kan configureerbaar product niet toevoegen aan winkelwagentje via GraphQL

De MDVA-37779 Adobe Commerce-patch lost het probleem op waarbij het onmogelijk is om een configureerbaar product aan winkelwagentje toe te voegen wanneer de website-id niet gelijk is aan de winkel-id. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 is geïnstalleerd. De patch-id is MDVA-3779. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.4.2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het is onmogelijk configureerbaar product aan het winkelwagentje toe te voegen wanneer de website-id niet gelijk is aan de winkel-id.

<u>Vereisten</u>:

Hebt u een tweede website, sla de weergave op en sla deze op waar de website-id niet gelijk is aan de winkel-id.

<u>Stappen om te reproduceren</u>:

1. Een leeg winkelwagentje maken met GraphQl-mutatie `createEmptyCart`.
1. Probeer een configureerbaar product aan de kar toe te voegen gebruikend `addConfigurableProductsToCart` mutatie.

<u>Verwachte resultaten</u>:

Product toegevoegd aan winkelwagentje.

<u>Werkelijke resultaten</u>:

Fout ophalen: *Kan het product met SKU xxxx niet toevoegen aan het winkelwagentje: de website met ID 3 die werd aangevraagd, is niet gevonden. Controleer de website en probeer het opnieuw.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.


## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
