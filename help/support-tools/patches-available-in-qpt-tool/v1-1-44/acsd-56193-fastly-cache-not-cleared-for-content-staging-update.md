---
title: 'ACSD-56193: [!DNL Fastly]  het geheime voorgeheugen wordt niet ontruimd voor inhoud die update opneemt'
description: Pas ACSD-56193 flard toe om de kwestie van Adobe Commerce te bevestigen waar het  [!DNL Fastly]  geheime voorgeheugen niet voor inhoud het opvoeren update wordt ontruimd.
feature: Cache, GraphQL, Staging
role: Admin, Developer
exl-id: d4bbfafa-2d24-44cf-a08b-f7dd9111a65b
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-56193: [!DNL Fastly] cache wordt niet gewist voor update van inhoudstaging

De ACSD-56193-patch verhelpt het probleem waarbij de [!DNL Fastly] -cache niet wordt gewist voor de update van de inhoudstaging. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 wordt geïnstalleerd. De patch-id is ACSD-56193. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De cache van [!DNL Fastly/Varnish] wordt niet gewist voor de update van de inhoudstaging

<u> Stappen om </u> te reproduceren:

1. Installeer en configureer [!DNL Varnish] cache.
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

1. Voer deze query meerdere keren uit en zorg ervoor dat de reactie in de [!DNL Varnish] in de cache is opgeslagen.
1. Voer het uitsnijden uit om de geplande wijziging toe te passen.
1. Voer de bovenstaande GraphQL-query opnieuw uit.
1. Maak een nieuw schema voor hetzelfde statische blok.
1. Herhaal de stappen met nummer 5-9.

<u> Verwachte resultaten </u>:

De bijgewerkte inhoud wordt geretourneerd nadat de geplande updates zijn uitgevoerd.

<u> Ware resultaten </u>:

De verouderde inhoud wordt geretourneerd nadat de geplande updates zijn uitgevoerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
