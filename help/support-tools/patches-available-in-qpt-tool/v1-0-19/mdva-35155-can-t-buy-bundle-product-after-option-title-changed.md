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

Met de MDVA-35155-patch wordt het probleem opgelost waarbij een bundelproduct niet kan worden gekocht nadat de optietitel is gewijzigd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 geïnstalleerd is. De patch-id is MDVA-35155. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over wolkeninfrastructuur 2.3.5

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.0-2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Bundelproducten kunnen niet worden gekocht nadat de titel van de optie is gewijzigd.

<u> Stappen om </u> te reproduceren:

1. Creeer een nieuw bundelproduct via **de Invoer van het Product**.
1. Het product is normaal in zowel de Admin als de frontend (in voorraad en kan aan de kar worden toegevoegd).
1. Werk hetzelfde product bij met wijzigingen in de naam in `bundle_values` en importeer het product opnieuw.

<u> Verwachte resultaten </u>:

De bestaande bundeloptie wordt bijgewerkt naar de nieuwe naam en behoudt dezelfde items in de nieuwe naam.

<u> Ware resultaten </u>:

* Admin probeert om producten met zelfde SKU in één enkel bundel-optie sectie samen te voegen, resulterend in een lege optiesectie.
* Het product heeft geen voorraad aan de voorzijde (zelfs na een herdex).

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
