---
title: "MDVA-35984: Onjuiste hoeveelheid product in gelijktijdige zendingen voor hetzelfde product"
description: De MDVA-35984-patch verhelpt het probleem bij het maken van meerdere gelijktijdige verzendingen voor hetzelfde product, waardoor een onjuiste producthoeveelheid (hoeveelheid) ontstaat. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 is geïnstalleerd. De patch-id is MDVA-35984. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: b15e25e1-c451-4350-950d-ae4893835e54
feature: Orders, Products, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# MDVA-35984: Onjuiste producthoeveelheid in gelijktijdige zendingen voor hetzelfde product

De MDVA-35984-patch verhelpt het probleem bij het maken van meerdere gelijktijdige verzendingen voor hetzelfde product, waardoor een onjuiste producthoeveelheid (hoeveelheid) ontstaat. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 geïnstalleerd is. De patch-id is MDVA-35984. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over wolkeninfrastructuur 2.4.2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.0-2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

1. Creeer een eenvoudig product met **Aantal** = *100*.
1. Maak twee bestellingen met dit product.
1. Maak gezamenlijke API vraag om verzendingen voor beide orden tot stand te brengen, zoals dit Voorbeeld:

   ```php
   POST <host>/rest/<store_code>/V1/order/3/ship    ```    where **order id** = *3* , with a payload like:    ```php    {        "items": [            {                "order_item_id": <order_item_id>,                "qty": 1            }        ],        "tracks": [            {                "track_number": "1Y-9876543210",                "title": "United Parcel Service",                "carrier_code": "ups"            }        ]    }
   ```

1. Controleer de producthoeveelheid in het beheerderster.

<u> Verwachte resultaten </u>:

Het resultaat is product **Aantal** = *98* na beide transporten.

<u> Ware resultaten </u>:

Het resultaat is product **Aantal** = *99* na beide transporten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
