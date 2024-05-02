---
title: 'ACSD-48773: e-mailsjabloon voor terugzendpunten uit verkeerde winkel'
description: Pas de ACSD-48773-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de sjabloon voor het e-mailadres wordt opgehaald uit de verkeerde winkel.
exl-id: 96dda97c-5177-4883-ad2b-709928cb5f4d
feature: Admin Workspace, Communications, Marketing Tools, Orders, Personalization, Rewards
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-48773: e-mailsjabloon voor terugzendpunten uit verkeerde winkel

De ACSD-48773-patch verhelpt het probleem waarbij de sjabloon voor bonuspunten uit de verkeerde winkel wordt gehaald. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 is geïnstalleerd. De patch-id is ACSD-48773. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De productprijsherdex werkt niet als het bundelproduct niet aan een website wordt toegewezen.

<u>Stappen om te reproduceren</u>:

1. Maak twee websites, twee winkels en twee winkelweergaven.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Reviews]** en **[!UICONTROL Reviews]**.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Store Email Addresses]**.
Schakel over naar de **[!DNL default website scope]** en stelt de **[!UICONTROL Customer Support Sender Email]** adres (bijvoorbeeld: *support_base@example.com*).
Schakel over naar de **[!DNL second website scope]** en stelt de **[!UICONTROL Customer Support Sender Email]** adres naar een andere waarde (bijvoorbeeld: *support_second@example.com*).
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** > **[!UICONTROL Share Customer Accounts]**, en instellen **[!UICONTROL Share Customer Accounts]** = *Per website*.
1. Onder **[!UICONTROL Reward Points]**, stelt u het volgende in:
   **[!UICONTROL Enable Reward Points Functionality]** = *Ja*
   **[!UICONTROL Enable Reward Points Functionality on Storefront]** = *Ja*
   **[!UICONTROL Actions for Acquiring Reward Points by Customers]** > **[!UICONTROL Review Submission]** en instellen **[!UICONTROL Review Submission]** = *150*
   **[!UICONTROL Email Notification Settings]** > **[!UICONTROL Email Sender]** en instellen **[!UICONTROL Email Sender]** = *Klantenondersteuning*
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** en de wisselkoersen voor de tweede website voor beide **[!UICONTROL Points/Currency]** en **[!UICONTROL Currency/Points]**.
1. Maak een klantenaccount op de tweede website.
1. Meld u aan als klant op de tweede website.
1. Zorg ervoor dat deze optie is ingeschakeld **[!UICONTROL Subscribe]** for **[!UICONTROL Balance Updates]**.
1. Stuur een productoverzicht.
1. Ga naar **[!UICONTROL Marketing]** > **[!UICONTROL User Content]** > **[!UICONTROL Pending Reviews]**.
1. De status van de nieuwe revisie wijzigen in ***[!UICONTROL Approved]*** en **[!UICONTROL Save]**.
1. Wacht tot het e-mailbericht is ontvangen.

<u>Verwachte resultaten</u>:

De e-mail met beloningspunten die is bijgewerkt, had moeten zijn verzonden door de e-mailafzender die is geconfigureerd voor het tweede websitebereik.

<u>Werkelijke resultaten</u>:

De e-mail met bonuspunten is verzonden door de e-mailafzender die is geconfigureerd voor het standaardbereik van de website.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
