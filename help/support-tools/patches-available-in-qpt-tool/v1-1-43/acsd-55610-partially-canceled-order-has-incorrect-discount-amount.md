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

De ACSD-55610-patch verhelpt het probleem waarbij een gedeeltelijk geannuleerde bestelling een onjuist kortingsbedrag heeft. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.43 wordt geïnstalleerd. De patch-id is ACSD-55610. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een gedeeltelijk geannuleerde order heeft een onjuist kortingsbedrag.

<u> Stappen om </u> te reproduceren:

1. Maak een winkelwagenprijsregel.

   * *[!UICONTROL Rule Name]*: *de Schaal van de Winter*
   * *[!UICONTROL Active]* = *ja*
   * *[!UICONTROL Websites]* = *Belangrijkste Website*
   * Kies alle klantengroepen.
   * Selecteer een specifieke coupon.
   * *[!UICONTROL Coupon Code]*: *WINTER10*
   * *[!UICONTROL Conditions]*: *[!UICONTROL If ALL of these conditions are TRUE]*: *Subtotal(Excl. Belasting) gelijk aan of groter dan 75*
   * Toepassen *[!UICONTROL Percent of product price discount]*.
   * *[!UICONTROL Discount Amount]*: *10*
   * *[!UICONTROL Discard subsequent rules]*: *ja*

1. Maak drie producten met een prijs van 100.
1. Voeg de drie producten toe aan het winkelwagentje.
1. Pas de coupon toe.
1. Plaats de bestelling.
1. Factuur één item van de bestelling en verzend het.
1. Annuleer de andere twee items.
1. Controleer de kolom `base_discount_canceled` .

<u> Verwachte resultaten </u>:

Het kortingsbedrag in `base_discount_cancelled` weerspiegelt correct.

<u> Ware resultaten </u>:

De instructie `base_discount_cancelled` is niet juist.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
