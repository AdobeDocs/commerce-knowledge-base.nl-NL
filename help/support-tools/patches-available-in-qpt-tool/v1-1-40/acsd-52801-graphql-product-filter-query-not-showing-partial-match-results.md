---
title: 'ACSD-52801: GraphQL-productfilterquery geeft resultaten van gedeeltelijke overeenkomsten niet weer'
description: Pas de ACSD-52801-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de GraphQL-productfilterquery geen resultaten van gedeeltelijke overeenkomst weergeeft.
feature: Products
role: Admin, Developer
exl-id: a03a4d09-ebec-4ad0-a875-48e000a29b44
source-git-commit: 40968db03939058884bca4e4aeed2ffef0462e0b
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# ACSD-52801: GraphQL-productfilterquery geeft resultaten van gedeeltelijke overeenkomsten niet weer

De ACSD-52801-patch verhelpt het probleem waarbij de GraphQL-productfilterquery geen resultaten toont die gedeeltelijk overeenkomen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 wordt geïnstalleerd. De patch-id is ACSD-52801. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2, 2.4.5-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De filterquery voor GraphQL-producten geeft geen resultaten weer die gedeeltelijk overeenkomen.

<u> Stappen om </u> te reproduceren:

1. Installeer een schone instantie met monstergegevens.
1. Voer de volgende GraphQL-query uit.

```GraphQL
{
  products(
    filter: { name: { match: "Life" } }
    sort: { position: ASC }
    pageSize: 100
    currentPage: 1
  ) {
    total_count
    items {
      url_key
      sku
      name
      meta_title
    }
  }
}
```

<u> Verwachte resultaten </u>:

Hiermee worden vergelijkbare resultaten als bij vooruitzoeken in de winkel mogelijk gemaakt door het attribuut `match_type` ([!UICONTROL PARTIAL], [!UICONTROL FULL] ) toe te voegen om de vereiste resultaten te bepalen. [!UICONTROL FULL] komt overeen met volledige woorden en [!UICONTROL PARTIAL] komt overeen met hele woorden, zoals leven in een leven lang.

<u> Ware resultaten </u>:

De vraag van de productfilter keert geen resultaten van gedeeltelijke gelijken voor onderzoekstrefwoorden terug.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
