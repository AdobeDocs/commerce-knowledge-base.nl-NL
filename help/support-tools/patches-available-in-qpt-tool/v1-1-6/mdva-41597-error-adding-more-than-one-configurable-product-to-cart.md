---
title: 'MDVA-41597: Fout bij het toevoegen van meerdere configureerbare producten aan winkelwagentje.'
description: Met de MDVA-41597-patch wordt het probleem opgelost waarbij gebruikers een fout krijgen wanneer ze meer dan één configureerbaar product met GraphQL aan het winkelwagentje toevoegen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6 is geïnstalleerd. De patch-id is MDVA-41597. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 777e0f9c-80e3-4cfb-9328-c20eb038f74a
feature: Configuration, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# MDVA-41597: Fout bij het toevoegen van meer dan één configureerbaar product aan winkelwagentje

Met de MDVA-41597-patch wordt het probleem opgelost waarbij gebruikers een fout krijgen wanneer ze meer dan één configureerbaar product met GraphQL aan het winkelwagentje toevoegen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6 is geïnstalleerd. De patch-id is MDVA-41597. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers krijgen een fout wanneer ze meer dan één configureerbaar product met GraphQL aan de winkelwagen toevoegen.

<u>Stappen om te reproduceren</u>:

Voeg meerdere configureerbare producten toe aan het winkelwagentje met GraphQL-mutatie: `addConfigurableProductsToCart`.

<u>Verwachte resultaten</u>:

Alle configureerbare producten worden toegevoegd aan de kar.

<u>Werkelijke resultaten</u>:

Alleen het eerste product wordt aan het winkelwagentje toegevoegd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
