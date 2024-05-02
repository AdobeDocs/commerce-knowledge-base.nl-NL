---
title: "MDVA-34943: Snelle orde kan 2+ producten aan kar niet toevoegen"
description: De MDVA-34943-patch lost het probleem op waarbij een snelle bestelling niet twee of meer producten aan het winkelwagentje kan toevoegen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.4.2.
exl-id: fcff6a78-fe00-4352-b0bc-149bd411d999
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# MDVA-34943: Snelle bestelling kan geen 2+ producten aan karretje toevoegen

De MDVA-34943-patch lost het probleem op waarbij een snelle bestelling niet twee of meer producten aan het winkelwagentje kan toevoegen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.4.0-p1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers kunnen niet snel twee of meer producten aan de winkelwagen toevoegen.

<u>Vereisten</u>:

Adobe Commerce met eenvoudige producten.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Snelle bestelling** op de Storefront (terwijl niet het programma geopend).
1. Ga geldige SKU in, klik het product dat op het autocomplete gebied verschijnt, en reeks **Aantal** = *1*.
1. Voer dezelfde geldige SKU in, maar wijzig het hoofdlettergebruik (hoofdletters wijzigen in kleine letters of kleine letters wijzigen in hoofdletters) van het eerste teken en klik op het product dat wordt weergegeven in het veld Automatisch aanvullen en stel **Aantal** = *1*.
1. Voer een `random_sting_value` for **SKU**, en instellen **Aantal** = *1*.
1. Set **SKU** = *123123123*, en instellen **Aantal** = *1*.
1. Alles verwijderen behalve het eerste item dat u aan het dialoogvenster **Snelle bestelling** pagina.
1. Ga 1st SKU (gelijkend op Stap 2 hierboven) in **Meerdere SKU&#39;s invoeren** en klik op **Toevoegen aan lijst**.
1. Dit resulteert in een hoeveelheid van 2 voor eerste SKU en een lijn voor a `random_sting_value`.
1. Vernieuw de pagina om meer te testen.
1. Dit resulteert in geen SKUs voor snelle orde, zoals verwacht.
1. Voer een `random_sting_value2` in de **Meerdere SKU&#39;s invoeren** en klik op **Toevoegen aan lijst**.
1. Dit resulteert in twee geldige SKU&#39;s van voor en a `random_sting_value2`.

<u>Verwachte resultaten</u>:

Twee of meer producten kunnen aan de kar worden toegevoegd, zoals verwacht.

<u>Werkelijke resultaten</u>:

Wanneer u naar de **Kar** , wordt het eerste toegevoegde product normaal weergegeven, maar voor het tweede product en alle volgende producten die aan het karretje worden toegevoegd, wordt een &quot;*1 product vereist aandacht*&#39;&#39; wordt weergegeven. De tweede of aanvullende producten worden vermeld op de **Product vereist aandacht** van de **Kar** pagina.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
