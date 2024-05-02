---
title: "MDVA-37478: Kan geen gedeeltelijke factuur maken via REST API"
description: De patch MDVA-37478 verhelpt het probleem wanneer u geen gedeeltelijke factuur kunt maken via REST API voor een bestelling die met betalingsmethode is geplaatst **Betaling op account**. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 is geïnstalleerd. De patch-id is MDVA-37478. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.
exl-id: 1b235baa-a188-467c-8ae5-de0836bc2caa
feature: REST, B2B, Invoices
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-37478: Kan geen gedeeltelijke factuur maken via REST API

De MDVA-37478-patch verhelpt het probleem wanneer u geen gedeeltelijke factuur kunt maken via REST API voor een bestelling die met een betalingsmethode is geplaatst **Betaling op rekening**. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 is geïnstalleerd. De patch-id is MDVA-37478. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

* De patch is ontworpen voor Adobe Commerce op cloud-infrastructuur 2.3.3-p1
* De patch is ook compatibel met Adobe Commerce op locatie en Adobe Commerce op cloud-infrastructuur 2.3.0-2.3.7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Vereiste</u>:

Adobe Commerce met geïnstalleerde B2B-module

<u>Stappen om te reproduceren</u>:

1. Inschakelen **B2B-bedrijf**.
1. Inschakelen **Betaling op rekening** betalingsmethode.
1. Maak twee eenvoudige producten.
1. Maak een bedrijfsaccount.
1. Voeg bedrijfskredieten toe die de totale prijs van 2 gecreëerde producten overschrijden.
1. Meld u aan bij de frontend met behulp van het gemaakte bedrijfsaccount.
1. Voeg de twee gemaakte producten toe aan het winkelwagentje en kassa met behulp van de **Betaling op rekening** betalingsmethode.
1. Probeer een gedeeltelijke factuur te maken voor de bestelling die via REST API is gemaakt:

   ```php
   POST /rest/V1/order//invoice
   {
     "items": [
       {
         "order_item_id": 2,
         "qty": 1
       }
     ]
   }
   ```

<u>Verwachte resultaten</u>:

De gedeeltelijke factuur wordt opgesteld voor een bestelling die is gemaakt met behulp van de **Betaling op rekening** betalingsmethode, zoals verwacht.

<u>Werkelijke resultaten</u>:

De volgende fout wordt geretourneerd door de REST API:

```php
{"message":"Invoice Document Validation Error(s):\nAn invoice for partial quantities cannot be issued for this order. To continue, change the specified quantity to the full quantity."}
```

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen, afhankelijk van uw Adobe Commerce-product:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
