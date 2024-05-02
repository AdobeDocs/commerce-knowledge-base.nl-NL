---
title: "ACSD-46617: **[!UICONTROL Continue to Checkout]** knoop grayed uit wanneer subtotaal groter dan gevormde minimum ordebedrag "
description: Pas de ACSD-46617-patch toe om het Adobe Commerce-probleem op te lossen waar de **[!UICONTROL Continue to Checkout]** de knoop wordt grayed uit zelfs als subtotal groter is dan de gevormde minimumordehoeveelheid.
exl-id: 42fe02bd-f48b-4c6d-8643-ea2c1aa98c94
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-46617: &quot;[!UICONTROL Continue to Checkout]&quot;-knop grijs als subtotaal groter is dan &quot;[!UICONTROL Minimum Order Amount]&quot;

Deze ACSD-46617-patch lost het probleem op waarbij de **[!UICONTROL Continue to Checkout]** de knoop wordt grijs uit zelfs als subtotal groter is dan de gevormde minimumordehoeveelheid. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 is geïnstalleerd. De patch-id is ACSD-46617. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De **[!UICONTROL Continue to Checkout]** de knoop wordt grijs uit zelfs als subtotal groter is dan de gevormde minimumordehoeveelheid.

<u>Stappen om te reproduceren</u>:

1. Ga naar Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** en stelt u het volgende in:
   * [!UICONTROL Enable]: *[!UICONTROL Yes]*
   * 
     [!UICONTROL Minimum Amount]: *2*

1. Een [!UICONTROL Cart Price Rule].
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
      * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
      * 
        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]: *[!UICONTROL Yes]*
1. Maak een product met een prijs van $25.
1. Voeg het product toe aan de kar.
1. Ga naar het winkelwagentje, selecteer de $5 **[!UICONTROL Flat Rate shipping]** en past u de couponcode toe.
1. Ga naar de kassa, voltooi de verzending en navigeer naar de **[!UICONTROL Paytment]** sectie.
1. Ga terug naar de winkelwagentje.

<u>Verwachte resultaten</u>:

Er is geen fout opgetreden met betrekking tot het minimale orderbedrag, aangezien het totaal van $2,4 groter is dan het vereiste bedrag van $2.

<u>Werkelijke resultaten</u>:

* Er is een fout opgetreden met betrekking tot het minimale orderbedrag, zelfs als het totaal van $2.4 groter is dan het minimale bestelbedrag van $2.
* De **[!UICONTROL Continue to Checkout]** wordt grijs weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
