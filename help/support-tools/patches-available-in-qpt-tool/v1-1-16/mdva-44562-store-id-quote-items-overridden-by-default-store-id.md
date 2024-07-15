---
title: 'MDVA-44562: Store id for quote items die zijn overschreven door standaard store id'
description: De patch MDVA-44562 verhelpt het probleem waarbij de standaard store-id de winkel-id overschrijft voor prijsaanhalingstekens voor GraphQL-aanvragen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 is geïnstalleerd. De patch-id is MDVA-44562. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
exl-id: 902bfc05-411d-4a6c-a6e8-cd7376629b0c
feature: Quotes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-44562: Winkel-id voor aanhalingstekens die standaard worden overschreven door winkel-id

De patch MDVA-44562 verhelpt het probleem waarbij de standaard store-id de winkel-id overschrijft voor prijsaanhalingstekens voor GraphQL-aanvragen. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 geïnstalleerd is. De patch-id is MDVA-44562. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De winkel-id voor aanhalingstekens wordt overschreven door de standaardopslagid voor GraphQL-aanvragen.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe winkelweergave.
1. Maak een nieuw eenvoudig product met verschillende namen per winkelweergave.
1. Maak een nieuwe klant.
1. Verkrijg het token voor klantautorisatie.

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. Creeer een nieuw citaat voor de klant gebruikend het toestemmingstoken.

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. Voeg een product toe aan de kar.

   ```GraphQL
   POST /rest/default/V1/carts/mine/items
   {
     "cartItem": {
       "sku": "simple1",
       "qty": 1,
       "quote_id": "1"
     }
   }
   ```

1. Haal de inhoud van het winkelwagentje op voor de standaardwinkelweergave.

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. Haal de inhoud van het winkelwagentje op voor de nieuwe winkelweergave.

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u> Verwachte resultaten </u>:

De reactie van de nieuwe winkelweergave toont de productnaam van de nieuwe winkelweergave.

<u> Ware resultaten </u>:

De reactie van de nieuwe archiefmening toont de productnaam opstelling onder de standaardarchiefmening.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
