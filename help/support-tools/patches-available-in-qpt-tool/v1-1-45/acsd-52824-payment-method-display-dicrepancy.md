---
title: "ACSD-52824: Uitgeschakelde betalingsmethoden weergegeven voor zakelijke klanten"
description: Pas de ACSD-52824-patch toe om het Adobe Commerce-probleem op te lossen, waarbij [!DNL PayPal Express], [!DNL Google Pay], and [!DNL Apple Pay] de betalingsmethoden worden voor de klanten van het bedrijf weergegeven , ook al zijn ze in de bedrijfsinstellingen uitgeschakeld .
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
exl-id: 03496fb1-d492-4f02-9cdc-466cb571a2eb
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-52824: Uitgeschakelde betalingsmethoden weergegeven voor zakelijke klanten

De ACSD-52824-patch verhelpt het probleem waarbij [!DNL PayPal Express], [!DNL Google Pay], en [!DNL Apple Pay] de betalingsmethoden worden voor de klanten van het bedrijf weergegeven , ook al zijn ze in de bedrijfsinstellingen uitgeschakeld . Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 is geïnstalleerd. De patch-id is ACSD-52824. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Uitgeschakelde betalingsmethoden worden weergegeven voor zakelijke klanten.

<u>Stappen om te reproduceren</u>:

1. Configureren en inschakelen [!DNL PayPal Express Checkout]. Navigeren naar **[!UICONTROL Basic Settings]** > selecteren **[!DNL PayPal Express Checkout]** en stelt de optie in voor **[!UICONTROL Display on Shopping Cart]** tot *Ja*.
1. Configureren [!DNL Braintree] en [!DNL Apple Pay] en [!DNL Google Pay] doorheen [!DNL Braintree].
1. Navigeren naar **[!UICONTROL Customers]** > **[!UICONTROL Companies]** en een nieuw bedrijf op te richten.
1. Klikken op **[!UICONTROL Advanced Settings]**, zoekt u de **[!UICONTROL Applicable Payment Methods]** en kiest u **[!UICONTROL Selected Payment Methods]**.
1. Onder **[!UICONTROL Selected Payment Methods]**, betalingsmethoden kiezen die zijn ingeschakeld en niet gekoppeld aan *[!DNL PayPal Express Checkout]*, *[!DNL Apple Pay]*, of *[!DNL Google Pay]*. Selecteer bijvoorbeeld **[!UICONTROL Check/Money Order]**.
1. Na het selecteren van de aangewezen betalingsmethodes, creeer een nieuwe klant en associeer hen met het eerder gecreeerde bedrijf.
1. Meld u aan bij de klantenaccount die aan het bedrijf is gekoppeld en ga verder met het toevoegen van items aan het winkelwagentje.
1. Let tijdens het afrekenen op de minikaart, winkelwagentje en de betalingsstap.

<u>Verwachte resultaten</u>:

Betalingsopties van [!DNL PayPal] en [!DNL Braintree] niet zichtbaar zijn in de mini-kart en het winkelwagentje.

<u>Werkelijke resultaten</u>:

Betalingsopties van [!DNL PayPal] en [!DNL Braintree] blijven zichtbaar in de mini - karretje en winkelwagentje .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
