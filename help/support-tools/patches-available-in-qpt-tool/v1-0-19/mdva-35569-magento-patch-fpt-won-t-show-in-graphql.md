---
title: "MDVA-35569: FPT zal niet worden getoond in GraphQL"
description: De patch MDVA-35569 lost het probleem op wanneer FPT (fixed product tax) in GraphQL niet wordt weergegeven wanneer de staat in het winkelwagentje is gespecificeerd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-35569. Het probleem is opgelost in Adobe Commerce versie 2.4.3.
exl-id: 3c38f7f9-9372-4f22-819c-c53efb9b5f78
feature: GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# MDVA-35569: FPT wordt niet weergegeven in GraphQL

De patch MDVA-35569 lost het probleem op wanneer FPT (fixed product tax) in GraphQL niet wordt weergegeven wanneer de staat in het winkelwagentje is gespecificeerd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 geïnstalleerd is. De patch-id is MDVA-35569. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur 2.3.4-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.4-2.4.1-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

1. FPT inschakelen.
1. Creeer een attribuut (Voorbeeld: *weee\_tax*).
1. Creeer een testproduct (Voorbeeld: *weetax*) met *weee\_tax* toegevoegde attribuut.
1. Wijs FPT aan Californië of aan een andere staat op *toe weee\_tax* attributen.
1. Maak een klant in GraphQL.
1. Maak een winkelwagen in GraphQL.
1. Voeg het *weetax* product aan de kar met GraphQL toe.
1. Vraag het winkelwagentje:

```php
{cart(cart_id: "xxx") {    items {    id    product {    name    sku    price_range {    minimum_price {    final_price {    value    }    fixed_product_taxes {    label    amount {    value    }    }    }    maximum_price {    final_price {    value    }    fixed_product_taxes {    label    amount {    value    }    }    }    }    }    prices {    price {    value    }    }    quantity    }    prices {    subtotal_excluding_tax {    value    }    applied_taxes {    amount {    value    }    }    grand_total {    value    currency    }    discounts {    amount {    value    }    label    }    }}}
```

<u> Verwachte resultaten </u>:

Het FPT zou normaal worden gevuld, zoals verwacht.

<u> Ware resultaten </u>:

* De FPT wordt niet gevuld met gegevens en is leeg.
* De vraag van het karretje geeft dit antwoord:

```php
{
 "data": {
 "cart": {
 "items": [
 {
 "id": "1",
 "product": {
 "name": "fpt",
 "sku": "fpt",
 "price_range": {
 "minimum_price": {
 "final_price": {
 "value": 10
 },
 "fixed_product_taxes": []
 },
 "maximum_price": {
 "final_price": {
 "value": 10
 },
 "fixed_product_taxes": []
 }
 }
 },
 "prices": {
 "price": {
 "value": 10
 }
 },
 "quantity": 1
 }
 ],
 "prices": {
 "subtotal_excluding_tax": {
 "value": 10
 },
 "applied_taxes": [],
 "grand_total": {
 "value": 21,
 "currency": "USD"
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
