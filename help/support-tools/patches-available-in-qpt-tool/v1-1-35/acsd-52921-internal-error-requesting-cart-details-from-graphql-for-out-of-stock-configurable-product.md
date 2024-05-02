---
title: "ACSD-52921: Fout bij het aanvragen van gegevens over winkelwagentjes bij GraphQL voor een configureerbaar product dat niet in voorraad is"
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

De ACSD-52921-patch verhelpt het probleem waarbij een interne fout optreedt bij het aanvragen van cartgegevens van GraphQL voor een product dat uit voorraad kan worden geconfigureerd. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.35 is geïnstalleerd. De patch-id is ACSD-52921. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treedt een interne fout op bij het aanvragen van gegevens over winkelwagentjes bij GraphQL voor een product dat niet in voorraad kan worden geconfigureerd.

<u>Stappen om te reproduceren</u>:

1. Maak een configureerbaar product met een paar opties.
1. Voeg een optie voor het bovengenoemde configureerbare product aan de kar van het frontend (gastcontrole) toe.
1. Krijg de `[ masked_id ]` van de `[ quote_id_mask ]` db lijst voor het bovengenoemde gecreeerde citaat.
1. Voer de volgende GraphQL vraag uit om de bovengenoemde details van het gastkarretje te krijgen.

   Voeg de `[ masked_id ]` ontvangen van stap 3 in de query.

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
1. Ga naar de back-end en werk de configureerbare producten bij *[!UICONTROL Stock Status]* tot *[!UICONTROL Out of Stock]*.
1. Voer dezelfde GraphQL-query uit, zoals in stap 4.

<u>Verwachte resultaten</u>:

Het foutbericht wordt correct verzonden/verwerkt in de reactie.

<u>Werkelijke resultaten</u>:

*500 interne server* Er wordt een fout gegenereerd als reactie op de GraphQL-query.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
