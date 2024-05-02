---
title: 'ACSD-51884: Pad naar cache van productafbeelding is onjuist voor opdracht vergroten/verkleinen'
description: Pas de ACSD-51884-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het cachepad voor de productafbeelding onjuist wordt nadat de opdracht resize is uitgevoerd.
feature: Products
role: Admin
exl-id: cf542c4b-07b1-4f05-95bc-82bc098bcd4d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-51884: Pad naar cache van productafbeelding is onjuist voor opdracht vergroten/verkleinen

De ACSD-51884-patch verhelpt het probleem waarbij een interne fout optreedt waarbij het cachepad voor de productafbeelding onjuist wordt nadat de opdracht resize is uitgevoerd. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.37 is geïnstalleerd. De patch-id is ACSD-51884. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7- 2.4.7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het cachepad voor productafbeeldingen wordt onjuist bij de opdracht vergroten/verkleinen.

<u>Stappen om te reproduceren</u>:

1. Nieuwe website/winkel/voorvertoning maken.
1. Maak een product en wijs het toe aan beide websites en upload de productafbeelding.
1. Maak een nieuw thema (zie bijgevoegde Adobe.zip).
1. In `app/design/Adobe/theme/etc/view.xml` wijzigen:

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">1</var>
</vars>
```

tot

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">0</var>
</vars>
```

1. Pas het thema toe op de eerder gemaakte storeview.
1. Controleer de productpagina op de tweede website. De afbeelding van het product wordt correct weergegeven.
1. Uitlijncache gebruiken:
   `bin/magento cache:flush`
1. Controleer de productpagina op de tweede website.

<u>Verwachte resultaten</u>:

De productafbeelding wordt correct weergegeven.

<u>Werkelijke resultaten</u>:

De productafbeelding bestaat niet.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
