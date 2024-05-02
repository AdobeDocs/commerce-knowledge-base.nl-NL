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

De MDVA-43862-patch lost het probleem op waarbij de klant geen winkelwagentjes kan bijwerken vanwege een GraphQL UpdateCartItems-mutatiefout. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 is geïnstalleerd. De patch-id is MDVA-43862. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1, 2.4.2-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De klant kan winkelwagentjes niet bijwerken vanwege een mutatiefout in GraphQL UpdateCartItems.

<u>Stappen om te reproduceren</u>:

1. Creeer een configureerbaar product (MH01) door één eenvoudig (MH01-XL-Grijs) toe te wijzen.
1. Ga naar Commerce Admin > **Catalogus** > **Producten** > **SKU** > **MH01** > **Aanpasbare opties**.
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

<u>Verwachte resultaten</u>:

Het winkelwagentje wordt zonder problemen bijgewerkt.

<u>Werkelijke resultaten</u>:

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

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
