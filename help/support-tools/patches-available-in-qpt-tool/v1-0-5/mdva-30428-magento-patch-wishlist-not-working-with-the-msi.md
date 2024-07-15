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

De MDVA-30428-patch lost de wenslijst op die niet werkt met Inventory management (MSI). Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 geïnstalleerd is.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3 - 2.3.3-p1 (QPT 1.0.6) en 2.3.5 - 2.4.1 (QPT 1.0.5)

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Bij het toevoegen van een product aan verlanglijst, wanneer het product aan een bron van de douaneinventaris wordt toegewezen, toont het volgende bericht &quot;*wij kunnen niet het punt aan Wish List nu toevoegen: Kan product zonder voorraad aan wenslijst toevoegen.*&quot;

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe inventarisbron in Commerce Admin. Voor stappen, verwijs naar [ Catalogus > Toevoegend een Nieuwe Source ](https://docs.magento.com/user-guide/catalog/inventory-sources-add.html?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=new%20inventory%20source) in onze gebruikersgids.
1. Maak een nieuwe voorraad in de Commerce Admin, wijs de nieuwe bron- en standaardwebsite toe aan de nieuwe voorraad. Voor stappen, verwijs naar [ Catalogus > Toevoegend een Nieuwe Voorraad ](https://docs.magento.com/user-guide/catalog/inventory-stock-add.html#add-new-stock) in onze gebruikersgids.
1. Maak een eenvoudig product en wijs de nieuwe voorraad alleen toe als voorraad.
1. Ga naar de pagina met eenvoudige productdetails op de voorzijde.
1. Voeg het product toe aan de verlanglijst. De volgende fout toont: *wij kunnen niet het punt aan Wish Lijst nu toevoegen: Kan product zonder voorraad niet toevoegen aan wenslijst*.

<u> Verwachte resultaten </u>:

Het product moet aan de verlanglijst worden toegevoegd met de aangepaste voorraad.

<u> Ware resultaten </u>:

Het product wordt niet toegevoegd aan de verlanglijst, en een foutenmelding toont.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
