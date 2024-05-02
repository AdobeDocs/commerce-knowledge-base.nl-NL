---
title: 'ACSD-55610: Gedeeltelijk geannuleerde bestelling heeft onjuist kortingsbedrag'
description: Pas de ACSD-55610-patch toe om het Adobe Commerce-probleem op te lossen wanneer een gedeeltelijk geannuleerde order een onjuist kortingsbedrag heeft.
feature: Invoices, Orders, Price Rules, Shopping Cart
role: Admin, Developer
exl-id: f4cca4fa-dc04-4c86-9176-c648b1d0e732
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-55610: Gedeeltelijk geannuleerde bestelling heeft onjuist kortingsbedrag

De ACSD-55610-patch verhelpt het probleem waarbij een gedeeltelijk geannuleerde bestelling een onjuist kortingsbedrag heeft. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.43 is geïnstalleerd. De patch-id is ACSD-55610. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een gedeeltelijk geannuleerde order heeft een onjuist kortingsbedrag.

<u>Stappen om te reproduceren</u>:

1. Maak een winkelwagenprijsregel.

   * *[!UICONTROL Rule Name]*: *Winter verkocht*
   * *[!UICONTROL Active]* = *Ja*
   * *[!UICONTROL Websites]* = *Hoofdwebsite*
   * Kies alle klantengroepen.
   * Selecteer een specifieke coupon.
   * *[!UICONTROL Coupon Code]*: *WINTER10*
   * *[!UICONTROL Conditions]*: *[!UICONTROL If ALL of these conditions are TRUE]*: *Subtotaal (behalve Belasting) gelijk aan of groter dan 75*
   * Toepassen *[!UICONTROL Percent of product price discount]*.
   * *[!UICONTROL Discount Amount]*: *10*
   * *[!UICONTROL Discard subsequent rules]*: *Ja*

1. Maak drie producten met een prijs van 100.
1. Voeg de drie producten toe aan het winkelwagentje.
1. Pas de coupon toe.
1. Plaats de bestelling.
1. Factuur één item van de bestelling en verzend het.
1. Annuleer de andere twee items.
1. Controleer de `base_discount_canceled` kolom.

<u>Verwachte resultaten</u>:

De kortingswaarde in `base_discount_cancelled` correct wordt weergegeven.

<u>Werkelijke resultaten</u>:

De `base_discount_cancelled` is niet juist.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
