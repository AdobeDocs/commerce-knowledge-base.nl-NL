---
title: 'ACSD-57394: Onjuiste productsortering door meerdere sorteerkenmerken in  [!DNL GraphQL]'
description: Pas ACSD-57394 flard toe om de kwestie van Adobe Commerce te bevestigen waar de producten verkeerd worden gesorteerd wanneer het gebruiken van veelvoudige soortattributen in  [!DNL GraphQL].
feature: GraphQL, Products
role: Admin, Developer
exl-id: f2e24daa-43a0-46b2-80b2-4e0ee116b776
source-git-commit: 42712af2ce4337cd64b8dea555139e4252fb91cf
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-57394: Onjuiste productsortering door meerdere sorteerkenmerken in [!DNL GraphQL]

De ACSD-57394-patch verhelpt het probleem waarbij producten onjuist worden gesorteerd wanneer meerdere sorteerkenmerken in [!DNL GraphQL] worden gebruikt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 wordt geïnstalleerd. De patch-id is ACSD-57394. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.5.0.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Producten worden onjuist gesorteerd wanneer meerdere sorteerkenmerken worden gebruikt in [!DNL GraphQL] .

<u> Stappen om </u> te reproduceren:

1. Maak een paar producten met verschillende prijzen en namen.
1. Maak een categorie en wijs de gemaakte producten eraan toe.
1. Verzend a [!DNL GraphQL] productvraag voor de gecreeerde categorie met enkele *soort* attributen. Bijvoorbeeld:

   ```
   {
   products(
     currentPage: 1
     pageSize: 10
     filter: {
       category_id: {
         eq :"3"
       }
     }
     sort: {  price: DESC, name: ASC, position: ASC
     }
   ){
   items{
     name
     sku
   
       price_range {
           minimum_price {
   
         regular_price {
           value
           currency
         }
         final_price {
           value
           currency
         }
         discount {
           amount_off
           percent_off
         }
               }
           }
      }
     }
    }
   ```

1. Controleer de reactie na het creëren van *soort* attributen.

<u> Verwachte resultaten </u>:

De producten moeten in de juiste volgorde worden geretourneerd. Het sorteren van de producten op veelvoudige attributen zou moeten werken.

<u> Ware resultaten </u>:

De producten worden niet in de juiste volgorde geretourneerd. Het sorteren van de producten op meerdere kenmerken werkt niet.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.

