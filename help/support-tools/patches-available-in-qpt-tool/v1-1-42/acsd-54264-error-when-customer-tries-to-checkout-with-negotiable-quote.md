---
title: 'ACSD-54264: Fout wanneer klant probeert uit te checken met een verhandelbaar prijsopgave.'
description: Pas de ACSD-54264-patch toe om het Adobe Commerce-probleem op te lossen waarbij het foutbericht "U kunt het gevraagde kenmerk niet bijwerken. Rij-id:store_id" wordt weergegeven wanneer een klant een aanhalingsteken in een andere winkelweergave wil uitchecken met een verhandelbaar aanhalingsteken.
feature: B2B, Checkout
role: Admin, Developer
exl-id: de8f451e-3b0a-4721-9ff4-18553477db1d
source-git-commit: 2e344b1ca4bc075bdbc9074bb431a398f0871698
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-54264: Fout verschijnt wanneer de klant probeert uit te checken met verhandelbare aanhalingstekens

Het ACSD-54264 flard lost de kwestie op waar een foutenmelding *u niet het gevraagde attribuut kunt bijwerken. Rij ID: store_id* verschijnt wanneer een klant probeert om met een verhandelbaar citaat van een andere archiefmening te controleren. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 wordt geïnstalleerd. De patch-id is ACSD-54264. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een foutenmelding *U kunt niet de gevraagde attributen bijwerken. Rij ID: store_id* verschijnt wanneer een klant probeert om met een verhandelbaar citaat van een andere archiefmening te controleren.

<u> Eerste vereisten </u>:

Adobe Commerce B2B-modules worden geïnstalleerd en ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Maak een extra winkelweergave voor de standaardwebsite.
1. Schakel *[!UICONTROL B2B Quote]* in de configuratie in.
1. Meld u aan als klant van een bedrijf in een van de winkelweergaven.
1. Voeg een product toe aan *[!UICONTROL Shopping Cart]*.
1. Het aanhalingsteken ter controle verzenden.
1. Als beheerder gaat u naar **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** en verzendt u het goedgekeurde aanhalingsteken.
1. Als bedrijfklant, verander de opslagmening in een verschillende archiefmening.
1. Probeer uit te checken.

<u> Verwachte resultaten </u>:

De klant plaatst een bestelling met dit citaat.

<u> Ware resultaten </u>:

* De fout treedt op bij het opslaan van de verzendgegevens:

  `You cannot update the request attribute. Row ID: store_id =#`

* De volgende fout wordt geregistreerd:

  `report.CRITICAL: Magento\Framework\Exception\InputException: You cannot update the requested attribute. Row ID: store_id = 2. in /app/code/Magento/NegotiableQuote/Plugin/Quote/Model/QuoteUpdateValidator.php:100`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
