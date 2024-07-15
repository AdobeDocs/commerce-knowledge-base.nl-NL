---
title: "MDVA-43862: klant kan winkelwagentjes niet bijwerken vanwege een mutatiefout in GraphQL UpdateCartItems"
description: De MDVA-43862-patch lost het probleem op waarbij de klant geen winkelwagentjes kan bijwerken vanwege een GraphQL UpdateCartItems-mutatiefout. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 is geïnstalleerd. De patch-id is MDVA-43862. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 5f0a2970-34a8-4a25-baf8-15c007f97084
feature: GraphQL, Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-43862: klant kan winkelwagentjes niet bijwerken vanwege een mutatiefout in GraphQL UpdateCartItems

De MDVA-43862-patch lost het probleem op waarbij de klant geen winkelwagentjes kan bijwerken vanwege een GraphQL UpdateCartItems-mutatiefout. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 geïnstalleerd is. De patch-id is MDVA-43862. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1, 2.4.2-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De klant kan winkelwagentjes niet bijwerken vanwege een mutatiefout in GraphQL UpdateCartItems.

<u> Stappen om </u> te reproduceren:

1. Creeer een configureerbaar product (MH01) door één eenvoudig (MH01-XL-Grijs) toe te wijzen.
1. Ga naar Commerce Admin > **Catalogus** > **Producten** > **SKU** > **MH01** > **Aanpasbare Opties**.
1. Voeg een aangepaste optie aan het product toe.
   * Optietitel: Option1
   * Type optie: Veld
   * Vereist: Ja
   * Prijs: 10,00
   * Prijstype: Vast
   * SKU: MHC1
   * Max. tekens: 25
1. Voer de onderstaande GraphQL-query uit om de winkelwagentje-id te genereren.

   ```GraphQL
   mutation {
     createEmptyCart
   }
   ```

1. Noteer de ID-code van het winkelwagentje.
1. Voer de onderstaande query uit om configureerbaar product aan de winkelwagentje toe te voegen:

   ```GraphQL
   mutation {
   addConfigurableProductsToCart(
   input: {
       cart_id: "<cart ID from above step>",
       cart_items: [{
       parent_sku: "MH01",
       data: {
           quantity: 1,
           sku: "MH01-XL-Gray"
           },
           customizable_options: {
               id: 1,
               value_string: "2"
               }
           }
       ]
   }
   )
   {
   cart {
     items {
       uid
       quantity
       product {
         name
         sku
       }
       ... on ConfigurableCartItem {
         configurable_options {
           option_label
         }
       }
     }
   }
   }
   }
   ```

1. U zult opmerken dat de kar met het configureerbare punt wordt bevolkt.
1. Noteer de geretourneerde uid.
1. Voer opnieuw de onderstaande query uit om het winkelwagentje bij te werken.

   ```GraphQL
   mutation {
     updateCartItems(
       input: {
         cart_id: "<cart ID from previous step>",
         cart_items: [
           {
             cart_item_uid: "<uid from previous step>"
             quantity: 3,
             customizable_options:[{
                 id: 1,
                 value_string: "67"
             }]
           }
         ]
       }
     ){
       cart {
         items {
           uid
           product {
             name
           }
           quantity
         }
         prices {
           grand_total{
             value
             currency
           }
         }
       }
     }
   }
   ```

1. Neem de reactie waar.

<u> Verwachte resultaten </u>:

Het winkelwagentje wordt zonder problemen bijgewerkt.

<u> Ware resultaten </u>:

De volgende fout treedt op:

```GraphQL
{
  "errors": [
    {
      "message": "Could not update cart item: You need to choose options for your item.",
      "extensions": {
        "category": "graphql-input"
      },
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "updateCartItems"
      ]
    }
  ],
  "data": {
    "updateCartItems": null
  }
}
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
