---
title: 'ACSD-50794: Kan cadeauverpakking niet verwijderen uit bestelling van klant via GraphQL'
description: Pas de ACSD-50794-patch toe om het Adobe Commerce-probleem op te lossen, waarbij gebruikers geen cadeauverpakking uit de bestelling van de klant via GraphQL kunnen verwijderen.
exl-id: 4983910c-9ea0-451e-a2b6-81485184bbce
feature: Gift, GraphQL, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-50794: Kan cadeauverpakking niet verwijderen uit bestelling van klant via GraphQL

De ACSD-50794-patch verhelpt het probleem waarbij gebruikers geen cadeauverpakking uit de bestelling van de klant via GraphQL kunnen verwijderen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 wordt geïnstalleerd. De patch-id is ACSD-50794. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers kunnen via GraphQL geen cadeauverpakking uit de bestelling van de klant verwijderen.

<u> Stappen om </u> te reproduceren:

1. Maak een klant van de voorzijde.
1. Maak een eenvoudig product.
1. Schakel *[!UICONTROL Gift Messages]* in door naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]** te gaan en *[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]* in te stellen.
1. Maak *[!UICONTROL Gift Wrapping]* door naar **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Gift Wrapping]** te gaan.
1. Haal klantentoken op.
1. Maak een leeg winkelwagentje, customerCart.
   * Producten aan de winkelwagentje toevoegen: `addProductsToCart` mutatie
   * Factureringsadres instellen: `setBillingAddressOnCart` mutatie
   * Verzendadres instellen: `setShippingAddressesOnCart` mutatie
   * Verzendmethode instellen: `setShippingMethodsOnCart` mutatie (afvlakking)
   * Betalingsmethode instellen: `setPaymentMethodOnCart` mutatie (checkmo)
1. Controleer nu het gift verpakken *Uid* met deze kartvraag:

   <pre><code class="language-GraphQL">
    {
      cart(cart_id: "{{CART_ID}}") {
        available_gift_wrappings{
            uid
        }
    }
    }
    </code></pre>

1. Stel de terugloop van cadeautjes in met `setGiftOptionsOnCart` .
1. Controleer het winkelwagentje: vraag naar winkelwagentje.
1. Schrijfterugloop ongedaan maken met `setGiftOptionsOnCart` (waarde instellen op null).
1. Kijk nogmaals naar het winkelwagentje: vraag naar het winkelwagentje.
1. Plaatsvolgorde: `placeOrder` mutatie.
1. Klantenquery uitvoeren: klant.

   <pre><code class="language-graphql">
    query {
      customer {
        firstname
        middlename
        lastname
        suffix
        email
        orders {
            items {
                order_date
                gift_wrapping {
                    design
                    uid
                }
            }
        }
        addresses {
          firstname
          middlename
          lastname
          street
          city
          region {
            region_code
            region
          }
          postcode
          country_code
          telephone
        }
      }
    }
    </code></pre>

<u> Verwachte resultaten </u>:

Zodra een gebruiker een geschenkomslag plaatst en het unsets, keert de klantenvraag ongeldig terug.

<u> Ware resultaten </u>:

De vraag van de klant keert nog gift terug zoals toegepast.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
