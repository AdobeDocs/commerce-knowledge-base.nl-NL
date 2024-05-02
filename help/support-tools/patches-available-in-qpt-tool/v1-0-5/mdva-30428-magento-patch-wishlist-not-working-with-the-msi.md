---
title: "MDVA-30428: wishlist not working with Inventory management"
description: De MDVA-30428-patch lost de wenslijst op die niet werkt met Inventory management (MSI). Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 is geïnstalleerd.
exl-id: 79e8d5d6-b073-48cf-8ecc-5c44667c12ad
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-30428: wenslijst werkt niet met Inventory management

De MDVA-30428-patch lost de wenslijst op die niet werkt met Inventory management (MSI). Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 is geïnstalleerd.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3 - 2.3.3-p1 (QPT 1.0.6) en 2.3.5 - 2.4.1 (QPT 1.0.5)

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u een product aan de verlanglijst toevoegt en het product aan een aangepaste inventarisbron wordt toegewezen, wordt het volgende bericht weergegeven: &quot;*Het object kan nu niet aan de Wish List worden toegevoegd. Kan product zonder voorraad niet aan de wenslijst toevoegen.*&quot;

<u>Stappen om te reproduceren</u>:

1. Maak een nieuwe inventarisbron in Commerce Admin. Raadpleeg voor stappen [Catalogus > Een nieuwe bron toevoegen](https://docs.magento.com/user-guide/catalog/inventory-sources-add.html?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=new%20inventory%20source) in onze gebruikershandleiding.
1. Maak een nieuwe voorraad in de Commerce Admin, wijs de nieuwe bron- en standaardwebsite toe aan de nieuwe voorraad. Raadpleeg voor stappen [Catalogus > Een nieuw bestand toevoegen](https://docs.magento.com/user-guide/catalog/inventory-stock-add.html#add-new-stock) in onze gebruikershandleiding.
1. Maak een eenvoudig product en wijs de nieuwe voorraad alleen toe als voorraad.
1. Ga naar de pagina met eenvoudige productdetails op de voorzijde.
1. Voeg het product toe aan de verlanglijst. De volgende fout laat zien: *Het object kan nu niet aan de Wish List worden toegevoegd. Kan product zonder voorraad niet toevoegen aan de wenslijst*.

<u>Verwachte resultaten</u>:

Het product moet aan de verlanglijst worden toegevoegd met de aangepaste voorraad.

<u>Werkelijke resultaten</u>:

Het product wordt niet toegevoegd aan de verlanglijst, en een foutenmelding toont.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
