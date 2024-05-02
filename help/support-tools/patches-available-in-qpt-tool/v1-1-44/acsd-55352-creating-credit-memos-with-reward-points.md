---
title: "ACSD-55352: Creditmemo's maken met bonuspunten"
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

De ACSD-55352-patch verhelpt het probleem dat na het maken van een gedeeltelijke creditnota met bonuspunten van de klant de status van de order verandert in *gesloten* en de opties voor creditnota verdwijnen van de beheerdersorteerpagina. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 is geïnstalleerd. De patch-id is ACSD-55352. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Na het maken van een gedeeltelijke creditnota met de punten van de klantenbeloning, verandert de ordestatus in *gesloten* en de opties voor creditnota verdwijnen van de beheerdersorteerpagina.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de Adobe Commerce-beheerder.
2. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]**.
3. Twee snelheden toevoegen:
   * *[!UICONTROL First]*:
      * *[!UICONTROL Direction]* = *Punten naar valuta*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
   * *[!UICONTROL Second]*:
      * *[!UICONTROL Direction]* = *Valuta naar punten*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
4. Een eenvoudig product maken met de prijs van *$ 100* en met *Aantal* : *100*.
5. Maak een klant van de winkel.
6. Ga opnieuw naar de achtergrond: **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** > Toevoegen *100* en sla de klant op.
7. Ga naar de winkel en login aangezien de klant eerder creeerde.
8. Het product toevoegen aan winkelwagentje met *Aantal* : *10*.
9. Ga naar **[!UICONTROL Checkout]** en gebruik de beschikbare *100* beloningspunten wanneer hierom wordt gevraagd en plaatsen de bestelling.
10. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]** en verzend die bestelling.
11. Ga naar [!UICONTROL Credit Memo] en de *Aantal naar restitutie* tot *8*.
12. Tik de **[!UICONTROL Refund Reward Points]** selectievakje en klik op **[!UICONTROL Refund offline]**.
13. Probeer de andere twee resterende producten van de bestelling terug te betalen met de [!UICONTROL Credit Memo].

<u>Verwachte resultaten</u>:

* De beheerder maakt [!UICONTROL Credit Memo] terugzending van de twee resterende producten.
* De orderstatus is *Voltooid*.

<u>Werkelijke resultaten</u>:

* Kan niet meer maken [!UICONTROL Credit Memo].
* De orderstatus is *Gesloten*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
