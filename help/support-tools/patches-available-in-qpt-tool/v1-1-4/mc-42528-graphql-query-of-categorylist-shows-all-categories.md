---
title: 'MC-42528: GraphQL query of categoryList toont alle categorieën'
description: De flard MC-42528 lost de kwestie op waar de vraag van GraphQL van ` categoryList' zowel toegewezen als niet toegewezen categorieën terugkeert wanneer de het doorbladeren Categorie van een bepaalde categorie aan "ontkent"wordt geplaatst. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 is geïnstalleerd. De patch-id is MC-42528. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 8bb29f43-92ae-4f37-b147-7121b55c185b
feature: Catalog Management, Categories, GraphQL, Customer Service
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MC-42528: De vraag van GraphQL van categoryList toont alle categorieën

De patch MC-42528 lost het probleem op waar de vraag van GraphQL van `categoryList` zowel toegewezen als niet toegewezen categorieën terugkeert wanneer de het Bladeren categorie van een bepaalde categorie aan &quot;ontkent&quot;wordt geplaatst. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 geïnstalleerd is. De patch-id is MC-42528. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

GraphQL-query van `categoryList` retourneert zowel toegewezen als niet-toegewezen categorieën.

<u> Stappen om </u> te reproduceren:

1. Maak twee categorieën, CAT1 en CAT2, en wijs weinig producten aan elke categorie toe.
1. Een persoonlijke gedeelde catalogus maken.
1. Maak een bedrijfgebruiker en wijs deze toe aan de gemaakte gedeelde catalogus.
1. Wijs CAT1 aan de douanecatalogus toe en plaats de categorietoestemming aan &quot;het Bladeren van Categorie&quot;voor de klantengroep van de privé catalogus toestaan.
1. Stel de categorietoestemming voor CAT2 in op Browsercategorie &quot;Weigeren&quot; voor de klantengroep van de persoonlijke catalogus.
1. Voer de `categoryList` - of `categories` GraphQL-query uit als bedrijfsgebruiker.

<u> Verwachte resultaten </u>:

Alleen de CAT1 wordt weergegeven in de reactie.

<u> Ware resultaten </u>:

Alle categorieën worden weergegeven in het antwoord, ongeacht de bladermachtigingen van de categorie.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
