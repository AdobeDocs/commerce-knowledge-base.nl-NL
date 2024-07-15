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

De MDVA-34665-patch verhelpt het probleem met ontbrekende gebundelde producten op categoriepagina&#39;s. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 geïnstalleerd is. De patch-id is MDVA-34665. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur 2.3.4-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.4-2.3.4-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

**Geval 1:**

<u> Eerste vereisten </u>:

1. Maak 15.000 gebundelde producten met één eenvoudig product als bundeloptie. Gebruik niet hetzelfde eenvoudige product met meerdere gebundelde producten.
1. De eenvoudige producten zouden aan *niet zichtbaar individueel* moeten worden geplaatst.

<u> Stappen om </u> te reproduceren:

1. Wijs 15.000 gebundelde producten in twee categorieën toe, 7.500 elk.
1. Selecteer alle eenvoudige producten (15 kB) en werk de voorraad bij met de updates voor productmassakenmerken. Ons doel is vele ids in de onderzoekCl- lijst (cl- lijsten zijn de lijsten die door de indexeerder worden gebruikt om te weten welke verslagen moeten worden bijgewerkt.)
1. Zorg ervoor dat de tabel `catalogsearch_fulltext_cl` 15.000 ID&#39;s bevat.
1. Zorg ervoor dat de `indexer_update_all_views` indexer wordt uitgevoerd.
1. Vraag de categoriepagina onophoudelijk en bekijk het productaantal.

<u> Verwachte resultaten </u>:

Het aantal producten moet onveranderd blijven na de herindexering.

<u> Ware resultaten </u>:

Het aantal producten daalt na een tijdje tot 7.450. Het blijft in 7.450, zelfs nadat het indexeren wordt gebeëindigd.

**Geval 2:**

<u> Stappen om </u> te reproduceren:

1. Maak als optie een bundelproduct met een bijbehorend eenvoudig product.
1. Verander de indexeerwijzen in *update op programma*.
1. Wijs het bundelproduct aan een categorie toe.
1. Verander de voorraadstatus van het eenvoudige product in *uit voorraad*.
1. Snijden uitvoeren; het bundelproduct verdwijnt uit de winkel.
1. Voeg de voorraad weer toe aan het eenvoudige product en sla deze op.
1. Uitvoeren van snijindex.
1. Vernieuw de categoriepagina.

<u> Verwachte resultaten </u>:

Het product is nog steeds afwezig.

<u> Ware resultaten </u>:

Bundel product wordt opnieuw weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
