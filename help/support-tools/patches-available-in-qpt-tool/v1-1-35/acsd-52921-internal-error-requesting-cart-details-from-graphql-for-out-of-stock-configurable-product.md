---
title: 'ACSD-52921: Fout bij het aanvragen van gegevens over winkelwagentjes bij GraphQL voor een configureerbaar product dat niet in voorraad is'
description: Pas de ACSD-52921-patch toe om het Adobe Commerce-probleem op te lossen wanneer een interne fout optreedt bij het aanvragen van cartdetails van GraphQL voor een product dat uit voorraad kan worden geconfigureerd.
feature: GraphQL, Configuration, Products, Shopping Cart
role: Admin
exl-id: 687460c4-f0d5-45d2-82b1-dda2947fe1e7
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-52921: Fout bij het aanvragen van gegevens over winkelwagentjes bij GraphQL voor een configureerbaar product dat niet in voorraad is

De ACSD-52921-patch verhelpt het probleem waarbij een interne fout optreedt bij het aanvragen van cartgegevens van GraphQL voor een product dat uit voorraad kan worden geconfigureerd. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-52921. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treedt een interne fout op bij het aanvragen van gegevens over winkelwagentjes bij GraphQL voor een product dat niet in voorraad kan worden geconfigureerd.

<u> Stappen om </u> te reproduceren:

1. Maak een configureerbaar product met een paar opties.
1. Voeg een optie voor het bovengenoemde configureerbare product aan de kar van het frontend (gastcontrole) toe.
1. Haal `[ masked_id ]` uit de `[ quote_id_mask ]` db lijst voor het bovengenoemde gecreeerde citaat.
1. Voer de volgende GraphQL vraag uit om de bovengenoemde details van het gastkarretje te krijgen.

   Voeg `[ masked_id ]` toe die van stap 3 in de vraag wordt ontvangen.

   ```GraphQL
   {
       cart(cart_id: "masked_id") {
           items {
               product {
                   name
                   sku
               }
               ... on ConfigurableCartItem {
                   configurable_options {
                       configurable_product_option_uid
                       option_label
                       configurable_product_option_value_uid
                       value_label
                   }
               }
               quantity
               errors {
                   code
                   message
               }
           }
       }
   }   
   ```

1. Hiermee worden de prijsgegevens zonder problemen geretourneerd.
1. Ga naar de backend en werk de configureerbare producten *[!UICONTROL Stock Status]* aan *[!UICONTROL Out of Stock]* bij.
1. Voer dezelfde GraphQL-query uit, zoals in stap 4.

<u> Verwachte resultaten </u>:

Het foutbericht wordt correct verzonden/verwerkt in de reactie.

<u> Ware resultaten </u>:

*500 de Interne fout van de Server* wordt geworpen in antwoord op de vraag van GraphQL.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
