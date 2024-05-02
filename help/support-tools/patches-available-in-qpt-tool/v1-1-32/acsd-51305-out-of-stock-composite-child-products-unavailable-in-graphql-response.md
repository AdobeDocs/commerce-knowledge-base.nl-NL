---
title: "ACSD-51305: niet-standaard samengestelde producten voor kinderen die niet beschikbaar zijn in GraphQL-reactie"
description: Pas de ACSD-51305-patch toe om het Adobe Commerce-probleem op te lossen wanneer samengestelde producten uit de voorraad niet beschikbaar zijn in de GraphQL-respons.
exl-id: 0f33eb62-dfd3-4d07-b095-9ee6e9983c4d
feature: Categories, GraphQL, Orders, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-51305: Niet in GraphQL-antwoord beschikbare samengestelde producten van buiten de voorraad

De ACSD-51305-patch verhelpt het probleem dat niet-standaard samengestelde onderliggende producten beschikbaar zijn in de GraphQL-respons. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 is geïnstalleerd. De patch-id is ACSD-51305. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Samengestelde onderliggende producten uit de voorraad zijn niet beschikbaar in de GraphQL-respons.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de beheerwebsite.
1. Maak een categorie (cat1, id=3).
1. Een *simple1* product (uit voorraad, niet afzonderlijk zichtbaar, toegewezen aan *kat1*).
1. Een *simple2* product (in voorraad, niet afzonderlijk zichtbaar, toegewezen aan *kat1*).
1. Een *bundel1* product met *simple1* en *simple2* onderliggende producten als keuzerondje *option1* producten en deze aan de *kat1* categorie.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]**.

   * Set **[!UICONTROL Display Out of Stock Products]** tot *Ja*.

1. Open de *bundel1* in de winkel, en ervoor zorgen dat beide *simple1* en *simple2* de kinderproducten worden getoond binnen het.
1. Voer de volgende GraphQL-query uit:

   ```GraphQL
   {
       categoryList(filters: { ids: { in: ["3"] } }) {
           id
           name
           products(pageSize: 8, sort: { position: ASC }) {
               total_count
               items {
                   id
                   sku
                   name
                   ... on BundleProduct {
                       url_key
                       items {
                           title
                           sku
                           options {
                               quantity
                               position
                               is_default
                               product {
                                   id
                                   name
                                   sku
                               }
                           }
                       }
                   }
               }
           }
       }
   }
   ```

<u>Verwachte resultaten</u>:

De **[!UICONTROL Product]** sectie in de **[!UICONTROL Options]** blok is niet leeg.

<u>Werkelijke resultaten</u>:

De **[!UICONTROL Product]** sectie in de **[!UICONTROL Options]** blok is leeg.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
