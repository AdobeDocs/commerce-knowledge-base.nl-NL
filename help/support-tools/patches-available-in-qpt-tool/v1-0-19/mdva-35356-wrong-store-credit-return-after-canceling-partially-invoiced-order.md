---
title: "MDVA-35356: Onjuist rendement van het klantenkrediet na annulering van gedeeltelijk gefactureerde bestelling"
description: De patch MDVA-35356 verhelpt het probleem met een onjuist rendement op het winkelkrediet nadat de bestelling gedeeltelijk is geannuleerd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-35356. Het probleem is opgelost in Adobe Commerce versie 2.4.3.
exl-id: af37f318-0818-4393-b768-939f08b73847
feature: Invoices, Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# MDVA-35356: Verkeerd rendement van winkelkrediet na annulering van gedeeltelijk gefactureerde bestelling

De patch MDVA-35356 verhelpt het probleem met een onjuist rendement op het winkelkrediet nadat de bestelling gedeeltelijk is geannuleerd. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-35356. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.0-2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Maak drie eenvoudige producten.
1. Een nieuwe gebruiker maken en winkelkrediet toewijzen (bijvoorbeeld: winkelkrediet = *$ 10,* eenvoudige productprijzen = *$ 100*, *$ 200*, en *$ 300*).
1. Meld u aan bij de bovenstaande gebruiker en voeg de drie producten toe aan het winkelwagentje.
1. Bekijk de drie producten in het winkelwagentje en gebruik het winkelkrediet voor een gedeelte van de bestelling (bijvoorbeeld: betaald met **Cheque/postwissel**).
1. Voer twee facturen op de bestelling uit via de API, één voor product 1 en één voor product 2:

   ```php
   //endpoint POST {\{baseUrl}}/V1/order/:orderId/invoice    //1st API call:    {    "capture": true,    "items": [    {    "order_item_id": 1,    "qty": 1    }    ],    "notify": true,    "appendComment": false    }    //2nd API call:    {    "capture": true,    "items": [    {    "order_item_id": 2,    "qty": 1    }    ],    "notify": true,    "appendComment": false    }
   ```

1. Het winkelkrediet wordt volledig toegepast op de eerste factuur.
1. &#x200B; Merk op dat het saldo van het winkelkrediet = *0*.
1. Annuleer de bestelling en controleer of twee items zijn gefactureerd en of het derde item is geannuleerd.
1. Bekijk het saldo van de winkelcreditering.

<u>Verwachte resultaten</u>:

Het creditsaldo van de winkel is nog steeds 0, omdat het winkelkrediet van 10 dollar is gefactureerd.

<u>Werkelijke resultaten</u>:

Het volledige winkelkrediet wordt teruggegeven: het saldo is $10.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
