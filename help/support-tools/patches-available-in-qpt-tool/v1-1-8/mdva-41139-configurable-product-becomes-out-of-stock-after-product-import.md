---
title: "MDVA-41139: configureerbaar product komt uit voorraad na import van product"
description: De MDVA-41139-patch verhelpt het probleem waarbij het configureerbare product na het importeren van het product uit voorraad raakt wanneer het eenvoudige product qty = 0 voor een van de bronnen is. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 is geïnstalleerd. De patch-id is MDVA-41139. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: e90ab578-50b9-4bc4-baf9-de4182e700ae
feature: Data Import/Export, Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-41139: configureerbaar product komt uit voorraad na import van product

De MDVA-41139-patch verhelpt het probleem waarbij het configureerbare product na het importeren van het product uit voorraad raakt wanneer het eenvoudige product qty = 0 voor een van de bronnen is. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 is geïnstalleerd. De patch-id is MDVA-41139. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het configureerbare product wordt uit voorraad na het importeren van het product wanneer het eenvoudige productaantal = 0 voor een van de bronnen.

<u>Vereisten</u>:

De inventarismodules worden geïnstalleerd.

<u>Stappen om te reproduceren</u>:

1. Maak een nieuwe bron en voorraad.
1. Creeer een configureerbaar product met kindproducten die aan de standaardbron en de nieuwe bron worden toegewezen.
1. Stel de waarde in van de standaardvoorraad voor elk onderliggende product = 0 en voor andere voorraad > 0.
1. Het configureerbare product is in voorraad.
1. Exporteer dit product en importeer het opnieuw.

<u>Verwachte resultaten</u>:

Het configureerbare product is in voorraad aangezien de tweede bron hoeveelheid > 0 heeft.

<u>Werkelijke resultaten</u>:

Het configureerbare product is uit voorraad.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
