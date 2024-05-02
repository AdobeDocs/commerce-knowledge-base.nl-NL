---
title: 'ACSD-52801: query voor GraphQL-productfilter waarbij resultaten van gedeeltelijke overeenkomsten niet worden weergegeven'
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

De ACSD-52801-patch verhelpt het probleem waarbij de GraphQL-productfilterquery geen resultaten toont die gedeeltelijk overeenkomen. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 is geïnstalleerd. De patch-id is ACSD-52801. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2, 2.4.5-p4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De filterquery voor GraphQL-producten geeft geen resultaten weer die gedeeltelijk overeenkomen.

<u>Stappen om te reproduceren</u>:

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

<u>Verwachte resultaten</u>:

Het staat gelijkaardige gelijke resultaten zoals in storefronvooruitonderzoek toe door toe te voegen `match_type` ([!UICONTROL PARTIAL], [!UICONTROL FULL]) om de vereiste resultaten te regelen. [!UICONTROL FULL] komt overeen met volledige woorden, en [!UICONTROL PARTIAL] komt overeen met woorden als leven in een leven lang.

<u>Werkelijke resultaten</u>:

De vraag van de productfilter keert geen resultaten van gedeeltelijke gelijken voor onderzoekstrefwoorden terug.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
