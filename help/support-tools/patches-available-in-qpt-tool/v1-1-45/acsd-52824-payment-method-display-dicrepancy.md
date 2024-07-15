---
title: "ACSD-52824: Uitgeschakelde betalingsmethoden weergegeven voor zakelijke klanten"
description: Pas ACSD-52824 flard toe om de kwestie van Adobe Commerce te bevestigen waar  [!DNL PayPal Express], [!DNL Google Pay], and [!DNL Apple Pay]  betalingsmethodes voor bedrijfklanten ondanks het worden onbruikbaar gemaakt in de bedrijfmontages verschijnen.
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
exl-id: 03496fb1-d492-4f02-9cdc-466cb571a2eb
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-52824: Uitgeschakelde betalingsmethoden weergegeven voor zakelijke klanten

De ACSD-52824-patch verhelpt het probleem waarbij [!DNL PayPal Express] -, [!DNL Google Pay] - en [!DNL Apple Pay] -betalingsmethoden worden weergegeven voor zakelijke klanten, hoewel deze zijn uitgeschakeld in de bedrijfsinstellingen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 wordt geïnstalleerd. De patch-id is ACSD-52824. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Uitgeschakelde betalingsmethoden worden weergegeven voor zakelijke klanten.

<u> Stappen om </u> te reproduceren:

1. Configureer en schakel [!DNL PayPal Express Checkout] in. Navigeer aan **[!UICONTROL Basic Settings]** > selecteer **[!DNL PayPal Express Checkout]** en plaats de optie voor **[!UICONTROL Display on Shopping Cart]** aan *ja*.
1. Configureer [!DNL Braintree] en schakel [!DNL Apple Pay] en [!DNL Google Pay] tot en met [!DNL Braintree] in.
1. Navigeer naar **[!UICONTROL Customers]** > **[!UICONTROL Companies]** en maak een nieuw bedrijf.
1. Klik op **[!UICONTROL Advanced Settings]** , zoek de **[!UICONTROL Applicable Payment Methods]** en kies **[!UICONTROL Selected Payment Methods]** .
1. Kies onder **[!UICONTROL Selected Payment Methods]** betalingsmethoden die zijn ingeschakeld en die niet zijn gekoppeld aan *[!DNL PayPal Express Checkout]* , *[!DNL Apple Pay]* of *[!DNL Google Pay]* . Selecteer bijvoorbeeld **[!UICONTROL Check/Money Order]** .
1. Na het selecteren van de aangewezen betalingsmethodes, creeer een nieuwe klant en associeer hen met het eerder gecreeerde bedrijf.
1. Meld u aan bij de klantenaccount die aan het bedrijf is gekoppeld en ga verder met het toevoegen van items aan het winkelwagentje.
1. Let tijdens het afrekenen op de minikaart, winkelwagentje en de betalingsstap.

<u> Verwachte resultaten </u>:

Betalingsopties van [!DNL PayPal] en [!DNL Braintree] zijn niet zichtbaar in de miniwinkelwagen en het winkelwagentje.

<u> Ware resultaten </u>:

Betalingsopties van [!DNL PayPal] en [!DNL Braintree] blijven zichtbaar in de miniwinkelwagen en het winkelwagentje.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
