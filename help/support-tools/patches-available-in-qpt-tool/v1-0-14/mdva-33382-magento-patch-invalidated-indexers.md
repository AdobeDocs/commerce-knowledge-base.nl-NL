---
title: 'MDVA-33382 patch: invalidate indexers'
description: De patch MDVA-33382 lost het probleem op wanneer indexeerders ongeldig worden gemaakt na het toevoegen, verwijderen of opnieuw ordenen van producten in een categorie. De ongeldig gemaakte indexeerders zijn "catalog_category_product `, catalogsearch_fulltext ` (en hun gebiedsdelen).
exl-id: b4ac10ee-0f9d-4d7a-be72-c4d90ebadb10
feature: Catalog Management, Categories, Price Indexer
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# MDVA-33382 patch: invalidate indexers

De patch MDVA-33382 lost het probleem op wanneer indexeerders ongeldig worden gemaakt na het toevoegen, verwijderen of opnieuw ordenen van producten in een categorie. De ongeldig gemaakte indexen zijn `catalog_category_product` , `catalogsearch_fulltext` (en de personen ten laste).

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 is geïnstalleerd. Het probleem wordt opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce op cloudinfrastructuur 2.3.4-p2

**Compatibel met Adobe Commerce-versies:** Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Alle indexeringsmodi instellen op **Update uitvoeren volgens schema**.
1. Een product uit een bewerkingspagina voor categorieën verwijderen.
1. Sla de categorie op.
1. Verifieer indices status of in achterste of in CLI.

<u>Verwachte resultaten</u>:

De volgende indices worden niet ongeldig gemaakt: `catalog_category_product` , `catalogsearch_fulltext` (en hun afhankelijke personen), zoals verwacht.

<u>Werkelijke resultaten</u>:

De volgende indices worden ongeldig gemaakt: `catalog_category_product` , `catalogsearch_fulltext` (en de personen ten laste).

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
