---
title: Klantgroepnamen, segmenten en informatie over de promotieregel die via  [!DNL GraphQL] wordt weergegeven
description: Dit artikel verstrekt hotfix om de blootstelling van de namen van de klantengroep, klantensegmenten, en de informatie van de promotieregel via  [!DNL GraphQL] te verhinderen.
feature: GraphQL
role: Admin, Developer
source-git-commit: f32085c80c9dbce513dad15ebf5f77a0e6398466
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# Klantgroepnamen, segmenten en informatie over de promotieregel die via [!DNL GraphQL] beschikbaar worden gemaakt

Dit artikel biedt een hotfix om te voorkomen dat namen van klantgroepen, klantsegmenten en informatie over promotieregel via [!DNL GraphQL] worden weergegeven. Het probleem zal volgens planning worden opgelost in Adobe Commerce 2.4.8-p1.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8

## Probleem

Voor [!UICONTROL Storefront Personalization Drop-ins] zijn nieuwe [!DNL GraphQL] -mutaties geïntroduceerd om basisinformatie weer te geven, zoals namen van klantgroepen, segmenten, winkelwagentjes en catalogusregels. Dit kan echter vertrouwelijke gegevens zoals aanbiedingsdetails of couponcodes blootstellen, als deze in de namen zijn opgenomen.

### Stappen om te reproduceren

#### Zaak I: [!UICONTROL Catalog Rule]

1. Voor *Admin* sidebar, ga **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Definieer de regelvoorwaarden (bijvoorbeeld productkenmerk of categorie).
1. Sla de regel op en pas deze toe.
1. Zorg ervoor dat een product voldoet aan de algemene voorwaarden.
1. Voer de volgende [!DNL GraphQL] query uit om alle regels op te halen:

   ```
   query {
       allCatalogRules {
           name
       }
   }
   ```

1. Vraag een product om te verifiëren of de regel van toepassing is:

   ```
   query {
       products(filter: { sku: { eq: "product-sku" } }) {
           items {
               name
               rules {
                   name
               }
           }
       }
   }
   ```

#### Zaak II: [!UICONTROL Cart Rule]

1. Voor *Admin* sidebar, ga **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Stel voorwaarden in, zoals minimumwaarde winkelwagentje en klantgroep.
1. Sla de regel op en pas deze toe.
1. Voeg producten toe aan winkelwagentje om de regel te activeren.
1. Gebruik [!DNL GraphQL] om alle regels voor het winkelwagentje te controleren:

   ```
   query {
       allCartRules {
           name
       }
   }
   ```

1. Controleer of er regels op het actieve winkelwagentje worden toegepast:

   ```
   query {
       cart(cart_id: "your-cart-id") {
           rules {
               name
           }
       }
   }
   ```

#### Zaak III: [!UICONTROL Customer Group]

1. Voor *Admin* sidebar, ga **[!UICONTROL Customers]** > **[!UICONTROL Customer Groups]**.
1. Controleer of de verwachte groepen bestaan.
1. Gebruik [!DNL GraphQL] om alle groepen op te halen:

   ```
   query {
       allCustomerGroups {
           name
       }
   }
   ```

1. Controleer de klant/gastgroep:

   ```
   query {
       customerGroup {
           name
       }
   }
   ```

#### Zaak IV: [!UICONTROL Customer Segment] (alleen voor Adobe Commerce)

1. Op *Admin* sidebar, ga **[!UICONTROL Customers]** > **[!UICONTROL Customer Segments]** → **[!UICONTROL Add Segment]**.
1. Bepaal op klant-gebaseerde voorwaarden (bijvoorbeeld, orde, kartinhoud).
1. Toepasselijk bereik toewijzen: *[!UICONTROL Visitor]*, *[!UICONTROL Registered]* of beide.
1. Zorg ervoor dat de voorwaarden overeenkomen met een testklant.
1. Gebruik [!DNL GraphQL] om alle segmenten te controleren:

   ```
   query {
       allCustomerSegments {
           name
           apply_to
       }
   }
   ```

1. Valideer de segmenten die op een winkelwagentje zijn toegepast:

   ```
   query {
       customerSegments(cartId: "your-cart-id") {
           name
       }
   }
   ```

<u> Verwacht resultaat </u>:

Namen van klantgroepen, segmenten en informatie over promotieregel worden niet via [!DNL GraphQL] weergegeven.

<u> Werkelijk resultaat </u>:

De namen van klantengroepen, segmenten, en de informatie van de promotieregel worden blootgesteld door [!DNL GraphQL].

## Oplossing

Pas de bijgevoegde patches toe, afhankelijk van uw Adobe Commerce-versie:

* Voor Adobe Commerce versie 2.4.8:

   * [LYNX-839_CE_2.4.8.patch](assets/LYNX-839_CE_2.4.8.patch.zip)
   * [LYNX-839_EE_2.4.8.patch](assets/LYNX-839_EE_2.4.8.patch.zip)

* Voor [!DNL Magento] Open Source versie 2.4.8:

   * [LYNX-839_CE_2.4.8.patch](assets/LYNX-839_CE_2.4.8.patch.zip)
