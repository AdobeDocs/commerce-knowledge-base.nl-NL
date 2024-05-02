---
title: "MDVA-35155: Kan het bundelproduct niet kopen nadat de optietitel is gewijzigd"
description: Met de MDVA-35155-patch wordt het probleem opgelost waarbij een bundelproduct niet kan worden gekocht nadat de optietitel is gewijzigd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-35155. Het probleem is opgelost in Adobe Commerce versie 2.4.3.
exl-id: 79770c69-1bb0-48d8-acdf-c8c1272f9da8
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-35155: Kan bundelproduct niet kopen nadat de optietitel is gewijzigd

Met de MDVA-35155-patch wordt het probleem opgelost waarbij een bundelproduct niet kan worden gekocht nadat de optietitel is gewijzigd. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-35155. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.3.5

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.0-2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Bundelproducten kunnen niet worden gekocht nadat de titel van de optie is gewijzigd.

<u>Stappen om te reproduceren</u>:

1. Een nieuw bundelproduct maken via **Product importeren**.
1. Het product is normaal in zowel de Admin als de frontend (in voorraad en kan aan de kar worden toegevoegd).
1. Hetzelfde product bijwerken met wijzigingen in de naam in `bundle_values` en importeer het product opnieuw.

<u>Verwachte resultaten</u>:

De bestaande bundeloptie wordt bijgewerkt naar de nieuwe naam en behoudt dezelfde items in de nieuwe naam.

<u>Werkelijke resultaten</u>:

* Admin probeert om producten met zelfde SKU in één enkel bundel-optie sectie samen te voegen, resulterend in een lege optiesectie.
* Het product heeft geen voorraad aan de voorzijde (zelfs na een herdex).

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
