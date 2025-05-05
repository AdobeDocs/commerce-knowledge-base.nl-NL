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

De ACSD-51884-patch verhelpt het probleem waarbij een interne fout optreedt waarbij het cachepad voor de productafbeelding onjuist wordt nadat de opdracht resize is uitgevoerd. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.37 wordt geïnstalleerd. De patch-id is ACSD-51884. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7- 2.4.7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het cachepad voor productafbeeldingen wordt onjuist bij de opdracht vergroten/verkleinen.

<u> Stappen om </u> te reproduceren:

1. Nieuwe website/winkel/voorvertoning maken.
1. Maak een product en wijs het toe aan beide websites en upload de productafbeelding.
1. Maak een nieuw thema (zie bijgevoegde Adobe.zip).
1. In `app/design/Adobe/theme/etc/view.xml` change:

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

<u> Verwachte resultaten </u>:

De productafbeelding wordt correct weergegeven.

<u> Ware resultaten </u>:

De productafbeelding bestaat niet.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
