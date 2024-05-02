---
title: "MDVA-31150: factuur zonder crediteringsgegevens van winkel"
description: De MDVA-31150-patch verhelpt het probleem waarbij een factuur wordt gemaakt zonder crediteringsgegevens van de winkel. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8 is geïnstalleerd. Het probleem wordt opgelost in Adobe Commerce versie 2.4.2.
exl-id: 70c87b67-6449-4285-9679-cca81613aa72
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-31150: factuur zonder crediteringsgegevens van winkel

De MDVA-31150-patch verhelpt het probleem waarbij een factuur wordt gemaakt zonder crediteringsgegevens van de winkel. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) versie 1.0.8 is geïnstalleerd. Het probleem wordt opgelost in Adobe Commerce versie 2.4.2.

## Betrokken producten en versies

* Deze patch is ontworpen voor Adobe Commerce op cloud-infrastructuur 2.3.5-p2.
* De patch is ook compatibel met Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.0 tot 2.3.5-p2 en 2.4.0 tot 2.4.0-p1.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Na de factuurvolgorde door de API zijn de gegevens van de gebruikte klantenbalans en de cadeaukaart niet aanwezig op de factuur.

<u>Stappen om te reproduceren</u>

1. Een crediteringsbedrag voor de winkel toevoegen aan een klantenaccount: Ga op de zijbalk Beheer naar **Klanten** > **Alle klanten.**
1. Zoek de klantrecord en klik op **Bewerken** in de kolom Actie, dan **Winkelkrediet** > De balans bijwerken > **Klant opslaan**.
1. Ga naar Storefront en voeg producten aan kar toe.
1. Plaats een bestelling door het bedrag van het winkelkrediet of de cadeaukaart als gedeeltelijke betaling toe te passen.
1. Een factuur maken met `REST API>POST>/rest/V1/order/1/invoice` met lading:    ```    { "capture": true, "items": [ { "extension_attributes": {}, "order_item_id": 3, "qty": 1 } ], "notify": true, "appendComment": true, "comment": { "extension_attributes": {}, "comment": "string", "is_visible_on_front": 0 }, "arguments": { "extension_attributes": {} }}    ```
1. De zojuist gemaakte factuur ophalen met `REST API>GET>/rest/V1/invoices/1`.

<u>Verwacht resultaat</u>

De creditering en het saldo van de kaartje van de opslag zijn teruggekeerd door de Vraag van API.

<u>Werkelijk resultaat</u>

De creditering en het saldo van de kaartje van de opslag zijn niet teruggekeerd door de Vraag van API.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
