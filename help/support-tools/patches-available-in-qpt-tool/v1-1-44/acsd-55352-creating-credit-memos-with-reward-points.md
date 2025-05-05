---
title: 'ACSD-55352: Creditmemo''s maken met beloningspunten'
description: Pas de ACSD-55352-patch toe om het Adobe Commerce-probleem op te lossen, waarbij na het maken van een gedeeltelijk creditmemo met bonuspunten van de klant de status van de order verandert in *closed* en de opties voor creditnota verdwijnen van de pagina voor bestellingen van de beheerder.
feature: Checkout, Orders
role: Admin, Developer
exl-id: 33ceb2e9-3cd5-4472-941a-e06c5c534f4a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# ACSD-55352: Creditmemo&#39;s maken met beloningspunten

ACSD-55352 herstelt de flard de kwestie waar na het creëren van een gedeeltelijk creditmemo met de punten van de klantenbeloning, de veranderingen van de ordestatus in *gesloten* en de opties van het creditmemo van de pagina van de adminorde verdwijnen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 wordt geïnstalleerd. De patch-id is ACSD-55352. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Na het creëren van een gedeeltelijk creditmemo met de punten van de klantenbeloning, verandert de status van de orde in *gesloten* en de opties van het creditmemo verdwijnen van de beheerderorde pagina.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij de Adobe Commerce-beheerder.
2. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]** .
3. Twee snelheden toevoegen:
   * *[!UICONTROL First]*:
      * *[!UICONTROL Direction]* = *Punten aan Valuta*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
   * *[!UICONTROL Second]*:
      * *[!UICONTROL Direction]* = *Valuta aan Punten*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
4. Creeer een eenvoudig product met de prijs van *$100* en met *Aantal*: *100*.
5. Maak een klant van de winkel.
6. Ga opnieuw naar de achtergrond: **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** > voeg *100* toe en sparen de klant.
7. Ga naar de winkel en login aangezien de klant eerder creeerde.
8. Voeg het product aan kar met *Aantal* toe: *10*.
9. Ga naar **[!UICONTROL Checkout]** en gebruik de beschikbare *100* beloningspunten wanneer ertoe aangezet en plaats de orde.
10. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]** en verzend die volgorde.
11. Ga naar [!UICONTROL Credit Memo] en werk *Aantal bij om* aan *8* terug te betalen.
12. Klik op het selectievakje **[!UICONTROL Refund Reward Points]** en klik op **[!UICONTROL Refund offline]** .
13. Probeer de andere twee resterende producten van de bestelling terug te betalen met de [!UICONTROL Credit Memo] .

<u> Verwachte resultaten </u>:

* De beheerder maakt [!UICONTROL Credit Memo] om de resterende twee producten te retourneren.
* De ordestatus is *Voltooid*.

<u> Ware resultaten </u>:

* Kan niet meer [!UICONTROL Credit Memo] maken.
* De ordestatus is *Gesloten*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
