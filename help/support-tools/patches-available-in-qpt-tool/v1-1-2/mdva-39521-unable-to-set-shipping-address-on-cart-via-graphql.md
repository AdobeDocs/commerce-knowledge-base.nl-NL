---
title: 'MDVA-39521: Verzendadres voor winkelwagentjes kan niet worden ingesteld via GraphQL'
description: De MDVA-39521-patch lost het probleem op waarbij de gebruiker geen verzendadres kan instellen op winkelwagentjes met een leeg telefoonnummer via GraphQL. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 is geïnstalleerd. De patch-id is MDVA-39521. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: b6bb4e83-ba65-4f15-82be-1252d9beb2fb
feature: GraphQL, Orders, Shipping/Delivery, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# MDVA-39521: Verzendadres voor winkelwagentjes kan niet worden ingesteld via GraphQL

De MDVA-39521-patch lost het probleem op waarbij de gebruiker geen verzendadres kan instellen op winkelwagentjes met een leeg telefoonnummer via GraphQL. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 geïnstalleerd is. De patch-id is MDVA-39521. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebruiker kan het verzendadres op de winkelwagentjes niet instellen met een leeg telefoonnummer via GraphQL, ondanks het feit dat de telefoon weergeven als optioneel is geconfigureerd.

<u> Stappen om </u> te reproduceren:

1. Maak een eenvoudig product.
1. Ga naar **Opslag** > **Configuratie** > **Klanten** > **de Configuratie van de Klant** > **Naam en de Opties van het Adres** en plaats de Show Telefoon als Facultatief.
1. Maak een leeg winkelwagentje via GraphQL-aanvraag.

   ```GraphQL
   mutation {
   createEmptyCart
   }
   ```

1. Product toevoegen aan winkelwagentje.

   ```GraphQL
   mutation {
   addSimpleProductsToCart(
   input: {
     cart_id: "{ CART_ID }"
     cart_items: [
       {
         data: {
           quantity: 1
           sku: "24-MG04"
         }
       }
     ]
   }
   ) {
   cart {
     items {
       id
       product {
         sku
         stock_status
       }
       quantity
     }
   }
   }
   }
   ```

1. Adres toevoegen: GRAPHQL VARIABLES.

   ```GraphQL
   {
     "cartId": "6Efw00UbjPoP5cvTFhsswDTjpxs0Xupt"
   }
   ```

   ```GraphQL
   mutation ($cartId: String!) {
     setShippingAddressesOnCart(input: {cart_id: $cartId, shipping_addresses:
     {address: {firstname: "John", lastname: "Doe", company: "Company Name",
     street: ["820 Burrard Street"], city: "Vancouver", region: "BC", postcode: "V6Z 2J1",
     country_code: "CA", telephone: "123-456-0000", save_in_address_book: false}}}) {
       cart {
         shipping_addresses {
           firstname
           lastname
           company
           street
           city
           postcode
           telephone
           country {
             code
             label
           }
         }
       }
     }
   }
   ```

   Resultaat

   ```GraphQL
     {
         "data": {
             "setShippingAddressesOnCart": {
                 "cart": {
                     "shipping_addresses": [
                         {
                             "firstname": "John",
                             "lastname": "Canada",
                             "company": "Company Name",
                             "street": [
                                 "820 Burrard Street"
                             ],
                             "city": "Vancouver",
                             "postcode": "V6Z 2J1",
                             "telephone": "123-456-0000",
                             "country": {
                                 "code": "CA",
                                 "label": "CA"
                             }
                         }
                     ]
                 }
             }
         }
     }
   ```

1. Voeg adres met leeg telefoonaantal toe.

   ```GraphQL
   mutation ($cartId: String!) {
     setShippingAddressesOnCart(input: {cart_id: $cartId, shipping_addresses: {address: {firstname:
       "John", lastname: "Canada", company: "Company Name", street: ["820 Burrard Street"], city:
       "Vancouver", region: "BC", postcode: "V6Z 2J1", country_code: "CA", telephone: "123-456-0000",
       save_in_address_book: false}}}) {
       cart {
         shipping_addresses {
           firstname
           lastname
           company
           street
           city
           postcode
           telephone
           country {
             code
             label
           }
         }
       }
     }
   }
   ```

<u> Verwachte resultaten </u>:

```GraphQL
 {
    "data": {
        "setShippingAddressesOnCart": {
            "cart": {
                "shipping_addresses": [
                    {
                        "firstname": "John",
                        "lastname": "Doe",
                        "company": "Company Name",
                        "street": [
                            "820 Burrard Street"
                        ],
                        "city": "Vancouver",
                        "postcode": "V6Z 2J1",
                        "telephone": "",
                        "country": {
                            "code": "CA",
                            "label": "CA"
                        }
                    }
                ]
            }
        }
    }
 }
```

<u> Ware resultaten </u>:

```GraphQL
{
    "data": {
        "setShippingAddressesOnCart": {
            "cart": {
                "shipping_addresses": []
            }
        }
    }
}
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitsflarden ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
