---
title: "MDVA-31224 patch: Product price redex take too long"
description: De MDVA-31224-patch lost het probleem op wanneer de herindexering van de productprijs te lang duurt om te voltooien of nooit voltooid is. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.7 is geïnstalleerd.
exl-id: 17f83fbf-9a43-4a65-b560-5f729b037c17
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# MDVA-31224 patch: Productprijsherdex duurt te lang

De MDVA-31224-patch lost het probleem op wanneer de herindexering van de productprijs te lang duurt om te voltooien of nooit voltooid is. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) versie 1.0.7 is geïnstalleerd.

## Betrokken producten en versies

* De patch is ontworpen voor Adobe Commerce op cloud-infrastructuur 2.3.3.
* De patch is ook compatibel met Adobe Commerce op locatie en Adobe Commerce op cloud-infrastructuur 2.3.3 - 2.3.4-p2.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het opnieuw berekenen van de productprijs duurt te lang om te voltooien of nooit te voltooien.

<u>Stappen om te reproduceren:</u>

1. Maak 6000 gebundelde producten met 15 opties.
1. Maak 1 gebundeld product met 30 opties.
1. Prijsherindex uitvoeren van CLI:     `bin/magento indexer:reindex catalog_product_price`

<u>Verwachte resultaten:</u>

Het opnieuw berekenen van de productprijs duurt 1,5 uur of langer.

<u>Werkelijke resultaten:</u>

Het opnieuw berekenen van de productprijs duurt kort (een minuut of twee) om te voltooien.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
