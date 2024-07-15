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

De MDVA-37779 Adobe Commerce-patch lost het probleem op waarbij het onmogelijk is om een configureerbaar product aan winkelwagentje toe te voegen wanneer de website-id niet gelijk is aan de winkel-id. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 geïnstalleerd is. De patch-id is MDVA-3779. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over wolkeninfrastructuur 2.4.2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het is onmogelijk configureerbaar product aan het winkelwagentje toe te voegen wanneer de website-id niet gelijk is aan de winkel-id.

<u> Eerste vereisten </u>:

Hebt u een tweede website, sla de weergave op en sla deze op waar de website-id niet gelijk is aan de winkel-id.

<u> Stappen om </u> te reproduceren:

1. Maak een leeg winkelwagentje met GraphQl-mutatie `createEmptyCart` .
1. Probeer met de `addConfigurableProductsToCart` -mutatie een configureerbaar product aan de wagen toe te voegen.

<u> Verwachte resultaten </u>:

Product toegevoegd aan winkelwagentje.

<u> Ware resultaten </u>:

Krijg een fout: *kon niet het product met SKU xxxx aan het het winkelwagentje toevoegen: De website met identiteitskaart 3 die werd gevraagd werd niet gevonden. Controleer de website en probeer het opnieuw.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.


## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar de [ flarden beschikbaar in het hulpmiddel QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
