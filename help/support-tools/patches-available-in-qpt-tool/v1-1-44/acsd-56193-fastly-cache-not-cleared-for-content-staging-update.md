---
title: '"ACSD-56193: [!DNL Fastly] cache is niet gewist voor update van inhoudstaging'''
description: Pas de ACSD-56193-patch toe om het Adobe Commerce-probleem op te lossen waarbij de [!DNL Fastly] cache is niet gewist voor update van inhoudstaging.
feature: Cache, GraphQL, Staging
role: Admin, Developer
exl-id: d4bbfafa-2d24-44cf-a08b-f7dd9111a65b
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-56193: [!DNL Fastly] cache is niet gewist voor update van inhoudstaging

De ACSD-56193-patch verhelpt het probleem waarbij de [!DNL Fastly] cache is niet gewist voor update van inhoudstaging. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 is geïnstalleerd. De patch-id is ACSD-56193. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De [!DNL Fastly/Varnish] cache is niet gewist voor update van inhoudstaging

<u>Stappen om te reproduceren</u>:

1. Installeren en configureren [!DNL Varnish] cache.
1. Maak een statisch blok met een geplande update.
1. Maak een categorie waarin het statische blok wordt ingesloten.
1. Zoek de inhoud van de categorie met de onderstaande GraphQL-query:

   ```GraphQL
      query GetCategories($id: String!) {
         categoryList(filters: { category_uid: { eq: $id } }) 
       {
           meta_title
           meta_keywords
           meta_description
           description
           path
           cms_block {
             content
             identifier
             title
             __typename
           }
           __typename
       }
     }
     {"id":"Mwo="}
   ```

1. Voer deze query meerdere keren uit en zorg ervoor dat de reactie in de cache is geplaatst [!DNL Varnish].
1. Voer het uitsnijden uit om de geplande wijziging toe te passen.
1. Voer de bovenstaande GraphQL-query opnieuw uit.
1. Maak een nieuw schema voor hetzelfde statische blok.
1. Herhaal de stappen met nummer 5-9.

<u>Verwachte resultaten</u>:

De bijgewerkte inhoud wordt geretourneerd nadat de geplande updates zijn uitgevoerd.

<u>Werkelijke resultaten</u>:

De verouderde inhoud wordt geretourneerd nadat de geplande updates zijn uitgevoerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
