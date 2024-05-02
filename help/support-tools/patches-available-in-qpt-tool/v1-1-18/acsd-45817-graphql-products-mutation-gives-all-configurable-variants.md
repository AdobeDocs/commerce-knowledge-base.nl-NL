---
title: 'ACSD-45817: mutatie in GraphQL-producten geeft alle configureerbare varianten.'
description: De ACSD-45817-patch verhelpt het probleem waarbij een GraphQL ` products'-mutatie voor een specifieke winkel alle configureerbare varianten retourneert, inclusief die welke niet aan de gevraagde winkel zijn toegewezen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 is geïnstalleerd. De patch-id is ACSD-45817. De kwestie is opgelost in Adobe Commerce 2.4.4.
exl-id: 3d61d1aa-36b5-471d-929b-7df8ce65c791
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-45817: mutatie in GraphQL-producten biedt alle configureerbare varianten

De ACSD-45817-patch verhelpt het probleem waarbij een GraphQL `products` de mutatie voor een specifieke opslag keert alle configureerbare varianten, met inbegrip van terug die niet aan de gevraagde opslag worden toegewezen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 is geïnstalleerd. De patch-id is ACSD-45817. De kwestie is opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

A GRAPHQL `products` de mutatie voor een specifieke opslag keert alle configureerbare varianten, met inbegrip van terug die niet aan de gevraagde opslag worden toegewezen.

<u>Vereisten</u>:

Maak een tweede website, tweede winkel en tweede winkelweergave.

<u>Stappen om te reproduceren</u>:

1. Creeer een configureerbaar product met twee subproducts: &quot;configureerbaar-a&quot;en &quot;configureerbaar-b&quot;.
1. Wijs het configureerbare product aan beide websites toe.
1. Wijs slechts één &quot;configureerbaar-a&quot;variatie aan de tweede website toe.
1. Ga naar de **Storefront**, overschakelen naar de tweede website en het configureerbare product openen.
1. Zorg ervoor dat er slechts één onderliggende optie wordt weergegeven: &quot;configureerbaar-a&quot;.
1. GraphQL-query uitvoeren met `POST: /graphql` eindpunt, en `Headers: "store" = "new"`

   ```GraphQL
   {
     products(filter: { sku: { eq: "configurable" } }) {
       items {
         id
         attribute_set_id
         name
         sku
         __typename
         price_range{
           minimum_price{
             regular_price{
               value
               currency
             }
           }
         }
         categories {
           id
         }
         ... on ConfigurableProduct {
           configurable_options {
             id
             attribute_id_v2
             label
             position
             use_default
             attribute_code
             values {
               value_index
               label
             }
             product_id
           }
           variants {
             product {
               id
               name
               sku
               attribute_set_id
               ... on PhysicalProductInterface {
                 weight
               }
               price_range{
                 minimum_price{
                   regular_price{
                     value
                     currency
                   }
                 }
               }
             }
             attributes {
               uid
               label
               code
               value_index
             }
           }
         }
       }
     }
   }
   ```

<u>Verwachte resultaten</u>:

De variatie &#39;configureerbaar-b&#39; wordt niet toegewezen aan de tweede website en moet niet worden weergegeven in de reactie.

<u>Werkelijke resultaten</u>:

De &quot;configureerbaar-b&quot;variatie wordt getoond in de reactie.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
