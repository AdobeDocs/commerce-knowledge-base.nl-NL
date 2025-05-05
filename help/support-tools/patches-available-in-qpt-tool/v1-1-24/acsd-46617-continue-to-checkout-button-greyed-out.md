---
title: 'ACSD-46617: **[!UICONTROL Continue to Checkout] ** knoop grayed uit wanneer subtotaal groter dan gevormde minimumordehoeveelheid'
description: Pas ACSD-46617 flard toe om de kwestie van Adobe Commerce op te lossen waar de **[!UICONTROL Continue to Checkout] ** knoop uit grayed is zelfs als subtotal groter is dan de gevormde minimumordehoeveelheid.
exl-id: 42fe02bd-f48b-4c6d-8643-ea2c1aa98c94
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-46617: &quot;[!UICONTROL Continue to Checkout]&quot;knoop grayed uit wanneer subtotal groter dan &quot;[!UICONTROL Minimum Order Amount]&quot;

Deze ACSD-46617-patch lost het probleem op waarbij de knop **[!UICONTROL Continue to Checkout]** grijs wordt weergegeven, zelfs als het subtotaal groter is dan de geconfigureerde minimale orderhoeveelheid. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 is geïnstalleerd. De patch-id is ACSD-46617. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De knop **[!UICONTROL Continue to Checkout]** wordt grijs weergegeven, zelfs als het subtotaal groter is dan de geconfigureerde minimumorderhoeveelheid.

<u> Stappen om </u> te reproduceren:

1. Ga naar Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** en stel het volgende in:
   * [!UICONTROL Enable]: *[!UICONTROL Yes]*
   * &#x200B;

     [!UICONTROL Minimum Amount]: *2*

1. Maak een [!UICONTROL Cart Price Rule] .
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
      * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
      * &#x200B;

        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]: *[!UICONTROL Yes]*
1. Maak een product met een prijs van $25.
1. Voeg het product toe aan de kar.
1. Ga naar het winkelwagentje, selecteer de methode $5 **[!UICONTROL Flat Rate shipping]** en pas de couponcode toe.
1. Ga naar de kassa, voltooi de verzending en navigeer naar de sectie **[!UICONTROL Paytment]** .
1. Ga terug naar de winkelwagentje.

<u> Verwachte resultaten </u>:

Er is geen fout opgetreden met betrekking tot het minimale orderbedrag, aangezien het totaal van $2,4 groter is dan het vereiste bedrag van $2.

<u> Ware resultaten </u>:

* Er is een fout opgetreden met betrekking tot het minimale orderbedrag, zelfs als het totaal van $2.4 groter is dan het minimale bestelbedrag van $2.
* De knop **[!UICONTROL Continue to Checkout]** wordt grijs weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
