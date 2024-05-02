---
title: 'MDVA-30972: bestelling status onjuiste verzending gemaakt via REST API'
description: Met de MDVA-30972-patch wordt het probleem opgelost waarbij de status van de bestelling onjuist wordt gewijzigd tijdens het maken van de zending via REST API. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd.
exl-id: 70b8db1f-16d0-48f4-b0a2-483a7176cb89
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-30972: bestelling status onjuiste verzending gemaakt via REST API

Met de MDVA-30972-patch wordt het probleem opgelost waarbij de status van de bestelling onjuist wordt gewijzigd tijdens het maken van de zending via REST API. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 tot 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer een gedeeltelijke verzending via REST API van Admin wordt gemaakt voor een bestelling met *Vermoedelijke fraude* orderstatus, de orderstatus wordt gewijzigd in *Verwerking*. Het moet blijven bij *Vermoedelijke fraude*.

<u>Vereisten</u>:

* PayPal EC of een andere online betalingsmethode is ingesteld.
* Integratie voor REST API is ingesteld.

<u>Stappen om te reproduceren</u>:

1. Maak een bestelling met twee of meer items.
1. Aanmelden bij **Beheerder** > **Verkoop** > **Orders**. Open de volgorde die u zojuist hebt gemaakt.
1. Schuif omlaag naar de pagina met orderdetails **Totaal van bestelling**. Klik op de knop **Status** vervolgkeuzelijst en selecteer *Vermoedelijke fraude*. Klik vervolgens op de knop **Opmerking verzenden** knop.
1. Controleer of de volgorde *Vermoedelijke fraude* status nu.
1. Een verzending maken voor één item van de bestelling met REST API:

   ```
   * Method = `Post`
   * Header = `"{host}/rest/V1/orders/ {order_id}/ship"`
   * Body =
   ```

   ```
    {      "items": [        {          "extension_attributes": {},          "order_item_id": {order_item_id},          "qty": 1        }      ]    }
   ```

1. Open de bestelling opnieuw in Beheer en controleer de status ervan.

<u>Verwachte resultaten</u>:

* Status van bestelling = *Vermoedelijke fraude*.
* De status van de bestelling wordt niet gewijzigd als dezelfde verzending wordt gemaakt via Admin.

<u>Werkelijke resultaten</u>:

Status van bestelling = *Verwerking*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
