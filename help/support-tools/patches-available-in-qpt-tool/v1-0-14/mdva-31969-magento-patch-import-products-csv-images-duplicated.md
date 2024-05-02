---
title: 'MDVA-31969 patch: import products .csv images duplicated'
description: De patch MDVA-31969 verhelpt het probleem waarbij afbeeldingen worden gedupliceerd bij het importeren van twee .csv-bestanden voor producten. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 is geïnstalleerd.
exl-id: 2a3c9cce-1f71-4f27-807e-12beffc379d2
feature: Data Import/Export, Products
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# MDVA-31969 patch: import products .csv images duplicated

De patch MDVA-31969 verhelpt het probleem waarbij afbeeldingen worden gedupliceerd bij het importeren van twee .csv-bestanden voor producten. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 is geïnstalleerd.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.3.4-p2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.3 - 2.3.4-p2, 2.4.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Nieuwe productafbeeldingen worden gemaakt in het dialoogvenster `pub/media` zelfs als dezelfde afbeelding al bestaat, bij het importeren van producten.

<u>Stappen om te reproduceren</u>:

1. Een map maken voor afbeeldingen: `mkdir var/import-images`
1. Afbeeldingen toevoegen binnen het pad `<install dir>/var/import-images`.
1. Importeer het CSV-bestand voor het product tweemaal.

<u>Verwachte resultaten</u>:

De producten eindigen met elke productafbeelding die eenmaal is gekoppeld.

<u>Werkelijke resultaten</u>:

Producten worden uiteindelijk gedupliceerd met productafbeeldingen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
