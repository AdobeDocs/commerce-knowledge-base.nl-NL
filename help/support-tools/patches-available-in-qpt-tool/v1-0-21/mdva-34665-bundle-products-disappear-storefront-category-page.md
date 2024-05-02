---
title: "MDVA-34665: bundelproducten verdwijnen op de pagina van de winkelcategorie"
description: De MDVA-34665-patch verhelpt het probleem met ontbrekende gebundelde producten op categoriepagina's. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 is geïnstalleerd. De patch-id is MDVA-34665. Het probleem is opgelost in Adobe Commerce versie 2.4.3.
exl-id: 2b393f91-de0d-4c54-89db-5e2af13f93a6
feature: Categories, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# MDVA-34665: bundelproducten verdwijnen op de pagina van de winkelcategorie

De MDVA-34665-patch verhelpt het probleem met ontbrekende gebundelde producten op categoriepagina&#39;s. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 is geïnstalleerd. De patch-id is MDVA-34665. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.3.4-p2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.4-2.3.4-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

**Zaak 1:**

<u>Vereisten</u>:

1. Maak 15.000 gebundelde producten met één eenvoudig product als bundeloptie. Gebruik niet hetzelfde eenvoudige product met meerdere gebundelde producten.
1. Eenvoudige producten moeten worden ingesteld op *Niet afzonderlijk zichtbaar*.

<u>Stappen om te reproduceren</u>:

1. Wijs 15.000 gebundelde producten in twee categorieën toe, 7.500 elk.
1. Selecteer alle eenvoudige producten (15 kB) en werk de voorraad bij met de updates voor productmassakenmerken. Ons doel is vele ids in de onderzoekCl- lijst (cl- lijsten zijn de lijsten die door de indexeerder worden gebruikt om te weten welke verslagen moeten worden bijgewerkt.)
1. Zorg ervoor dat u 15.000 id&#39;s in de `catalogsearch_fulltext_cl` tabel.
1. Zorg ervoor dat de `indexer_update_all_views` indexer wordt uitgevoerd.
1. Vraag de categoriepagina onophoudelijk en bekijk het productaantal.

<u>Verwachte resultaten</u>:

Het aantal producten moet onveranderd blijven na de herindexering.

<u>Werkelijke resultaten</u>:

Het aantal producten daalt na een tijdje tot 7.450. Het blijft in 7.450, zelfs nadat het indexeren wordt gebeëindigd.

**Zaak 2:**

<u>Stappen om te reproduceren</u>:

1. Maak als optie een bundelproduct met een bijbehorend eenvoudig product.
1. Indexeermodi wijzigen in *bijwerken volgens schema*.
1. Wijs het bundelproduct aan een categorie toe.
1. Wijzig de voorraadstatus van het eenvoudige product in *uit voorraad*.
1. Snijden uitvoeren; het bundelproduct verdwijnt uit de winkel.
1. Voeg de voorraad weer toe aan het eenvoudige product en sla deze op.
1. Uitvoeren van snijindex.
1. Vernieuw de categoriepagina.

<u>Verwachte resultaten</u>:

Het product is nog steeds afwezig.

<u>Werkelijke resultaten</u>:

Bundel product wordt opnieuw weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
