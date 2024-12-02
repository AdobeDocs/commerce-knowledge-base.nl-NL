---
title: 'ACSD-45817: mutatie in GraphQL-producten biedt alle configureerbare varianten'
description: De ACSD-45817-patch verhelpt het probleem waarbij een GraphQL ` products'-mutatie voor een specifieke winkel alle configureerbare varianten retourneert, inclusief die welke niet aan de gevraagde winkel zijn toegewezen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 is geïnstalleerd. De patch-id is ACSD-45817. De kwestie is opgelost in Adobe Commerce 2.4.4.
exl-id: 3d61d1aa-36b5-471d-929b-7df8ce65c791
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-45817: mutatie in GraphQL-producten biedt alle configureerbare varianten

De ACSD-45817-patch verhelpt het probleem waarbij een GraphQL `products` -mutatie voor een specifieke winkel alle configureerbare varianten retourneert, inclusief varianten die niet aan de gevraagde winkel zijn toegewezen. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 geïnstalleerd is. De patch-id is ACSD-45817. De kwestie is opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een GraphQL `products` -mutatie voor een specifieke store retourneert alle configureerbare varianten, inclusief varianten die niet aan de gevraagde store zijn toegewezen.

<u> Eerste vereisten </u>:

Maak een tweede website, tweede winkel en tweede winkelweergave.

<u> Stappen om </u> te reproduceren:

1. Creeer een configureerbaar product met twee subproducts: &quot;configureerbaar-a&quot;en &quot;configureerbaar-b&quot;.
1. Wijs het configureerbare product aan beide websites toe.
1. Wijs slechts één &quot;configureerbaar-a&quot;variatie aan de tweede website toe.
1. Ga naar **Storefront**, schakelaar aan de tweede website, en open het configureerbare product.
1. Zorg ervoor dat er slechts één onderliggende optie wordt weergegeven: &quot;configureerbaar-a&quot;.
1. Een GraphQL-query uitvoeren met het `POST: /graphql` -eindpunt en `Headers: "store" = "new"`

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

<u> Verwachte resultaten </u>:

De variatie &#39;configureerbaar-b&#39; wordt niet toegewezen aan de tweede website en moet niet worden weergegeven in de reactie.

<u> Ware resultaten </u>:

De &quot;configureerbaar-b&quot;variatie wordt getoond in de reactie.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in onze ontwikkelaarsdocumentatie.
