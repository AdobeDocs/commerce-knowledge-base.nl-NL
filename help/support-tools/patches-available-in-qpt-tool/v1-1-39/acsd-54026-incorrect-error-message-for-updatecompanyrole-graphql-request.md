---
title: 'ACSD-54026: onjuist foutbericht voor GraphQL-verzoek updateCompanyRole'
description: Pas de ACSD-54026-patch toe om het Adobe Commerce-probleem op te lossen wanneer er een onjuist foutbericht is voor een updateCompanyRole GraphQL-verzoek voor een niet-geautoriseerde gebruiker.
feature: Roles/Permissions
role: Admin, Developer
exl-id: c18a8815-975a-499d-a372-8635d89aa673
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-54026: Onjuist foutbericht voor `updateCompanyRole` GraphQL-aanvraag

De ACSD-54026-patch verhelpt het probleem bij een onjuist foutbericht voor een `updateCompanyRole` GraphQL-aanvraag voor een niet-geautoriseerde gebruiker. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.39 wordt geïnstalleerd. De patch-id is ACSD-54026. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er wordt een onjuist foutbericht weergegeven voor een `updateCompanyRole` GraphQL-aanvraag voor een niet-geautoriseerde gebruiker.

<u> Stappen om </u> te reproduceren:

1. B2B-bedrijf inschakelen in configuratie.
1. Maak een bedrijf.
1. Verzend een `updateCompanyRole` GraphQL-aanvraag zonder een token voor toonder door te geven of met een ongeldige token voor toonder.
1. Bekijk het foutbericht in het GraphQL-antwoord.

<u> Verwachte resultaten </u>:

U krijgt het volgende foutenbericht: *de huidige klant is niet geautoriseerd.*

<u> Ware resultaten </u>:

U krijgt het volgende foutenbericht: *de Klant is geen bedrijfgebruiker.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
