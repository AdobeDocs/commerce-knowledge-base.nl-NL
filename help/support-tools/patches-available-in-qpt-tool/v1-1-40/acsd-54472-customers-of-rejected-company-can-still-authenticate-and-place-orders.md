---
title: 'ACSD-54472: klanten van een afgewezen bedrijf kunnen nog steeds verifiëren'
description: Pas de ACSD-54472-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de klanten van een afgewezen bedrijf nog steeds kunnen verifiëren en klanten van een geblokkeerd en afgewezen bedrijf nog steeds orders kunnen plaatsen.
feature: B2B
role: Admin, Developer
exl-id: 76fc4553-02b1-4563-91a9-0cda99fa4c7d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-54472: klanten van een afgewezen bedrijf kunnen nog steeds verifiëren

De ACSD-54472-patch verhelpt het probleem dat klanten van een afgewezen bedrijf nog steeds kunnen verifiëren en dat klanten van een geblokkeerd en afgewezen bedrijf nog steeds orders kunnen plaatsen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 wordt geïnstalleerd. De patch-id is ACSD-54472. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De klanten van een verworpen bedrijf kunnen nog voor authentiek verklaren, en de klanten van een geblokkeerd en verworpen bedrijf kunnen nog orden plaatsen.

<u> Stappen om </u> te reproduceren:

1. Maak een bedrijf.
1. Voeg producten toe aan het winkelwagentje via [!DNL GraphQL] .
1. Verander de bedrijfstatus in *Geblokkeerd*.
1. Verzend een [!DNL GraphQL] -verzoek om de bestelling te plaatsen en een aanhalingsteken voor onderhandelingen te maken.
1. Verander de bedrijfstatus in *Afgewezen*.
1. Verzend een [!DNL GraphQL] -aanvraag om de token voor de gebruikersautorisatie van het bedrijf op te halen.
1. Plaats klantenstatus aan *Inactief*.
1. Verzend een [!DNL GraphQL] -aanvraag om de token voor de gebruikersautorisatie van het bedrijf op te halen.

<u> Verwachte resultaten </u>:

* De orde en het onderhandelbare citaat worden niet geplaatst door de gebruiker van het *Geblokkeerde* bedrijf.
* Het teken van de vergunning wordt niet verkregen voor de gebruiker van het *Verworpen* bedrijf.
* Het teken van de vergunning wordt niet verkregen voor de *Inactieve* klant.

<u> Ware resultaten </u>:

* De orde en het onderhandelbare citaat worden geplaatst door de gebruiker van het *Geblokkeerde* bedrijf.
* Het teken van de vergunning wordt verkregen voor de gebruiker van het *Verworpen* bedrijf.
* Het teken van de vergunning wordt verkregen voor de *Inactieve* klant.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
