---
title: 'ACSD-46683: Verzendprijs toont *Nog niet berekend*'
description: Pas de ACSD-46683-patch toe om het Adobe Commerce-probleem op te lossen waarbij de verzendprijs *Nog niet berekend* wordt weergegeven.
exl-id: 77986612-87b7-4f50-afaf-1cfe9a4feb6f
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-46683: De verzendprijs toont *nog niet berekend*

ACSD-46683 flardfixes de kwestie waar de verschepende prijs *nog niet berekend* toont. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 wordt geïnstalleerd. De patch-id is ACSD-46683. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De het verschepen prijs toont *nog niet berekend*.

<u> Eerste vereisten </u>:

Adobe Commerce Inventory management-modules (MSI) zijn geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Creeer een eenvoudig product en plaats zijn prijs aan *$34*.
1. Configureer de methode voor gratis verzending.
1. Vorm minstens één meer leveringsmethode.
1. Ga naar **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** en maak een nieuwe regel:
   * Naam = *75more*
   * Coupon = Geen
   * Prioriteit = 1
   * Voorwaarden: Subtotaal is gelijk aan of groter dan *$75*
   * Handelingen:
      * Toepassen op verzendbedrag = Ja
      * Verdere regels negeren = Nee
      * Gratis verzending = voor verzendingen met overeenkomende objecten
1. Een andere regel voor de winkelwagenprijs maken:
   * Naam = *35off*
   * Prioriteit = 0
   * Coupon = specifieke coupon
   * Couponcode = 35off
   * Handelingen:
      * Toepassen = Percentage van korting op productprijs
      * Korting = 35
      * Toepassen op verzendbedrag = Nee
      * Verdere regels negeren = Ja
      * Gratis verzending = Nee
1. Open de winkel en voeg drie producten toe aan de winkelwagen, zodat het subtotaal meer dan $75 bedraagt.
1. Ga verder met uitchecken als gast.
1. Selecteer bij de verzendstap **$0 - gratis verzending** en ga verder met de betalingsstap.
1. Controleer [!UICONTROL Order Summary] op de betalingsstap. Het toont *[!UICONTROL $0 - Free Shipping - Free]*.
1. Pas de couponcode *35off* toe, zal het subtotal bijwerken en het minder dan $75 maken.
1. Controleer [!UICONTROL Order Summary] op de betalingsstap.

<u> Verwachte resultaten </u>:

Het volgende bericht wordt getoond: *Geselecteerde verschepende methode is niet beschikbaar. Selecteer een andere verzendmethode voor deze bestelling.*

<u> Ware resultaten </u>:

De het verschepen prijsvertoningen *nog niet berekend*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
