---
title: "MDVA-43102: Aankoopbare hoeveelheid niet correct bijgewerkt"
description: De MDVA-43102-patch verhelpt het probleem dat de verkoopbare hoeveelheid niet correct wordt bijgewerkt wanneer de restitutie via REST API wordt uitgevoerd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 is geïnstalleerd. De patch-id is MDVA-43102. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: c51bc45b-a7e0-4581-a318-9c4736e6661c
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-43102: verkoopbare hoeveelheid niet correct bijgewerkt

De MDVA-43102-patch verhelpt het probleem dat de verkoopbare hoeveelheid niet correct wordt bijgewerkt wanneer de restitutie via REST API wordt uitgevoerd. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 is geïnstalleerd. De patch-id is MDVA-43102. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.1 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het verkoopbare aantal wordt niet correct bijgewerkt wanneer een terugbetaling met REST API wordt gedaan.

<u>Stappen om te reproduceren</u>:

1. Voeg een item aan het winkelwagentje toe.
1. Controleer de voorraadhoeveelheid en de koopste hoeveelheid.
1. Maak een bestelling.
1. Maak indien nodig een factuur.
1. Verzend een REST-verzoek om de factuur terug te betalen met de volgende lading:

   * offline methode/volgorde/`<order_id>`/restitutie
   * online methode/factuur/`<invoice_id>`/restitutie

   ```rest
   {
     "items": [
     {
       "order_item_id": <order_item_id>,
       "qty": 1
     }
     ],
     "notify": true,
     "arguments": {
       "shipping_amount": 5,
       "extension_attributes": {
         "return_to_stock_items": [
         <order_item_id>
         ]
       }
     }
   }
   ```

1. Verzend de objecten niet.
1. Vergelijk de voorraadhoeveelheid en de Salable Qty van voordien. Beide moeten met hetzelfde bedrag worden bijgewerkt.

<u>Verwachte resultaten</u>:

De verkoopbare hoeveelheid wordt correct bijgewerkt wanneer een restitutie wordt afgegeven voordat de bestelling wordt verzonden en het product aan de voorraad wordt teruggegeven.

<u>Werkelijke resultaten</u>:

De verkoopbare hoeveelheid wordt niet bijgewerkt wanneer een restitutie wordt afgegeven voordat de bestelling wordt verzonden en het product wordt teruggebracht naar de voorraad.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
