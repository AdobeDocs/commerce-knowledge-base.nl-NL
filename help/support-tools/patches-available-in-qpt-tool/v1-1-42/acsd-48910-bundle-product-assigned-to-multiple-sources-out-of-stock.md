---
title: 'ACSD-48910: Gebundeld product met meerdere bronnen heeft geen voorraad na factuur en verzending'
description: Pas de ACSD-48910-patch toe om het Adobe Commerce-probleem op te lossen waarbij het gebundelde product dat aan meerdere bronnen is toegewezen, uit voorraad raakt nadat een bestelling is gefactureerd en verzonden, zelfs als het nog steeds een hoeveelheid heeft die niet gelijk is aan nul.
feature: Products, Inventory
role: Admin, Developer
exl-id: 6ac3dedf-1c28-4874-b963-44a429b37983
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-48910: Gebundeld product met meerdere bronnen heeft geen voorraad na factuur en verzending

De ACSD-48910-patch verhelpt de kwestie waar het gebundelde product dat aan meerdere bronnen is toegewezen uit voorraad komt nadat een bestelling is gefactureerd en verzonden, zelfs als het nog steeds een hoeveelheid heeft die niet gelijk is aan nul. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 wordt geïnstalleerd. De patch-id is ACSD-48910. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het gebundelde product dat aan veelvoudige bronnen wordt toegewezen gaat uit voorraad na facturering en verzending, zelfs als het nog beschikbaar is.

<u> Stappen om </u> te reproduceren:

1. Maak twee websites.
1. Maak twee weergaven voor winkels/winkels (één per website).
1. Maak twee eenvoudige producten (qty = 10) en wijs deze toe aan zowel voorraden als websites.
1. Maak een gebundeld product en voeg deze eenvoudige producten eraan toe. Wijs het gebundelde product aan beide websites toe.
1. Ga naar de winkel en voeg het gebundelde product aan de kar toe.
1. Check uit en plaats de bestelling.
1. Van Admin, factuur en verzend de orde.

<u> Verwachte resultaten </u>:

Het gebundelde product blijft in voorraad omdat we slechts 1 van de 10 artikelen hebben gekocht.

<u> Ware resultaten </u>:

Het gebundelde product wijzigt zijn status in out-of-stock.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
