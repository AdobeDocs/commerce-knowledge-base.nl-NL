---
title: "ACSD-49574: Kan cadeaukaartproduct in winkelwagentje niet bijwerken via GraphQL"
description: Pas de ACSD-49574-patch toe om het Adobe Commerce-probleem op te lossen waarbij een cadeaukaartproduct niet via GraphQL in het winkelwagentje kan worden bijgewerkt.
exl-id: e446128f-c991-4c3c-8d1c-bbff6230e448
feature: Admin Workspace, Gift, GraphQL, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-49574: Kan cadeaukaartproduct in winkelwagentje niet bijwerken via GraphQL

De ACSD-49574-patch verhelpt het probleem dat een cadeaukaartproduct niet via GraphQL in het winkelwagentje kan worden bijgewerkt. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 is geïnstalleerd. De patch-id is ACSD-49574. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een cadeaukaartproduct kan niet via GraphQL worden bijgewerkt in het winkelwagentje.

<u>Stappen om te reproduceren</u>:

1. Maak een cadeaukaartproduct.
1. Voeg het cadeaukaartproduct via GraphQL toe aan het winkelwagentje.
1. Probeer productvelden van cadeaukaarten via GraphQL bij te werken `updateCartItems` mutatie.

   Voorbeeld van GraphQL-gebruik:

   ```GraphQL
   mutation ($cartId: String!, $cartItems: [CartItemUpdateInput!]!){
       updateCartItems(
           input: {
               cart_id: $cartId,
               cart_items: $cartItems
           }
       )   {
           cart {
               id
               items {
                   uid
                   quantity
                   product {
                       sku
                   }
                   ... on GiftCardCartItem {
                       sender_name
                       sender_email
                       recipient_name
                       recipient_email
                       message
                       amount {
                           value
                           currency
                       }
                   }
               }
           }
       }
   }
   
   variables
   {
       "cartId": "sDrOu06VYlGejhDivQMcnmcNPSxTMUDd",
       "cartItems": [
           {
               "cart_item_id": 113,
               "quantity": 1,
               "customizable_options": [{
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfc2VuZGVyX25hbWU=",
                       "value_string": "sender_name"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfc2VuZGVyX2VtYWls",
                       "value_string": "sender_email"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfcmVjaXBpZW50X25hbWU=",
                       "value_string": "recipient name"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfcmVjaXBpZW50X2VtYWls",
                       "value_string": "recipient_email"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvZ2lmdGNhcmRfbWVzc2FnZQ==",
                       "value_string": "message"
                   },
                   {
                       "uid": "Z2lmdGNhcmQvY3VzdG9tX2dpZnRjYXJkX2Ftb3VudA==",
                       "value_string": "10"
                   }
               ]
           }]
   }
   ```

<u>Verwachte resultaten</u>:

Alle productvelden van de cadeaukaart (sender_name, sender_email, receiving_name, receiving_email, message, amount) worden bijgewerkt met `updateCartItems` mutatie.

<u>Werkelijke resultaten</u>:

Alleen het bedrag wordt bijgewerkt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
