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

De MDVA-34943-patch lost het probleem op waarbij een snelle bestelling niet twee of meer producten aan het winkelwagentje kan toevoegen. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17 geïnstalleerd is. Het probleem is opgelost in Adobe Commerce versie 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur 2.4.0-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers kunnen niet snel twee of meer producten aan de winkelwagen toevoegen.

<u> Eerste vereisten </u>:

Adobe Commerce met eenvoudige producten.

<u> Stappen om </u> te reproduceren:

1. Ga naar **Snelle Orde** op de Storefront (terwijl niet het programma geopend).
1. Ga geldige SKU in, klik het product dat op het autocomplete gebied verschijnt, en reeks **Hoeveelheid** = *1*.
1. Ga zelfde geldige SKU in, maar verander het geval (verandering in hoofdletters in kleine letters, of verandering in kleine letters in hoofdletters) van het eerste karakter, en klik het product dat op het autocomplete gebied verschijnt, en reeks **Aantal** = *1*.
1. Ga a `random_sting_value` voor **SKU** in, en reeks **Hoeveelheid** = *1*.
1. Plaats **SKU** = *123123123*, en reeks **Hoeveelheid** = *1*.
1. Schrap alles behalve de eerste ingang u aan de **Snelle pagina van de Orde** toevoegde.
1. Ga 1st SKU (gelijkend op Stap 2 hierboven) in het **Veelvoudige SKUs** gebied in, en klik **toevoegen aan Lijst**.
1. Dit resulteert in een hoeveelheid van 2 voor eerste SKU en een lijn voor a `random_sting_value`.
1. Vernieuw de pagina om meer te testen.
1. Dit resulteert in geen SKUs voor snelle orde, zoals verwacht.
1. Ga a `random_sting_value2` in het **Veelvoudige gebied van SKUs** in, en klik **toevoegen aan Lijst**.
1. Dit resulteert in twee geldige SKU&#39;s van voor en a `random_sting_value2`.

<u> Verwachte resultaten </u>:

Twee of meer producten kunnen aan de kar worden toegevoegd, zoals verwacht.

<u> Ware resultaten </u>:

Wanneer genomen aan de **pagina van het Kart**, verschijnt het eerste toegevoegde product normaal, maar voor het tweede product en om het even welke verdere die producten aan de kar worden toegevoegd, a &quot;*1 product vereist aandacht*&quot;foutenmelding verschijnt. De tweede of om het even welke extra producten zullen op het **Product worden vermeld vereist Aandacht** sectie van de **** pagina van het Kaart.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
