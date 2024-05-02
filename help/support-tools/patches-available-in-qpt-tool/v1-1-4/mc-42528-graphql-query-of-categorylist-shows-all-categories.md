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

De MC-42528-patch lost het probleem op waarbij de GraphQL-query op `categoryList` Hiermee worden zowel toegewezen als niet-toegewezen categorieën geretourneerd wanneer de categorie Bladeren van een bepaalde categorie is ingesteld op Weigeren. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 is geïnstalleerd. De patch-id is MC-42528. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

GraphQL-query van `categoryList` retourneert zowel toegewezen als niet-toegewezen categorieën.

<u>Stappen om te reproduceren</u>:

1. Maak twee categorieën, CAT1 en CAT2, en wijs weinig producten aan elke categorie toe.
1. Een persoonlijke gedeelde catalogus maken.
1. Maak een bedrijfgebruiker en wijs deze toe aan de gemaakte gedeelde catalogus.
1. Wijs CAT1 aan de douanecatalogus toe en plaats de categorietoestemming aan &quot;het Bladeren van Categorie&quot;voor de klantengroep van de privé catalogus toestaan.
1. Stel de categorietoestemming voor CAT2 in op Browsercategorie &quot;Weigeren&quot; voor de klantengroep van de persoonlijke catalogus.
1. Voer de `categoryList` of `categories` GraphQL vraagt als bedrijfgebruiker.

<u>Verwachte resultaten</u>:

Alleen de CAT1 wordt weergegeven in de reactie.

<u>Werkelijke resultaten</u>:

Alle categorieën worden weergegeven in het antwoord, ongeacht de bladermachtigingen van de categorie.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
