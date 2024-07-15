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

De ACSD-48773-patch verhelpt het probleem waarbij de sjabloon voor bonuspunten uit de verkeerde winkel wordt gehaald. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 wordt geïnstalleerd. De patch-id is ACSD-48773. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De productprijsherdex werkt niet als het bundelproduct niet aan een website wordt toegewezen.

<u> Stappen om </u> te reproduceren:

1. Maak twee websites, twee winkels en twee winkelweergaven.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Reviews]** en schakel **[!UICONTROL Reviews]** in.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Store Email Addresses]** .
Ga naar **[!DNL default website scope]**, en plaats het **[!UICONTROL Customer Support Sender Email]** adres, (bijvoorbeeld: *support_base@example.com*).
Schakelaar aan **[!DNL second website scope]**, en plaats het **[!UICONTROL Customer Support Sender Email]** adres aan een andere waarde (bijvoorbeeld: *support_second@example.com*).
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** > **[!UICONTROL Share Customer Accounts]**, en reeks **[!UICONTROL Share Customer Accounts]** = *per Website*.
1. Stel onder **[!UICONTROL Reward Points]** het volgende in:
   **[!UICONTROL Enable Reward Points Functionality]** = *ja*
   **[!UICONTROL Enable Reward Points Functionality on Storefront]** = *ja*
   **[!UICONTROL Actions for Acquiring Reward Points by Customers]** > **[!UICONTROL Review Submission]** en reeks **[!UICONTROL Review Submission]** = *150*
   **[!UICONTROL Email Notification Settings]** > **[!UICONTROL Email Sender]** en reeks **[!UICONTROL Email Sender]** = *Klantenondersteuning*
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** en stel de wisselkoersen voor de tweede website in voor zowel **[!UICONTROL Points/Currency]** als **[!UICONTROL Currency/Points]** .
1. Maak een klantenaccount op de tweede website.
1. Meld u aan als klant op de tweede website.
1. Zorg ervoor dat u **[!UICONTROL Subscribe]** for **[!UICONTROL Balance Updates]** inschakelt.
1. Stuur een productoverzicht.
1. Ga naar **[!UICONTROL Marketing]** > **[!UICONTROL User Content]** > **[!UICONTROL Pending Reviews]** .
1. Wijzig de status van de nieuwe revisie in ***[!UICONTROL Approved]*** en **[!UICONTROL Save]** .
1. Wacht tot het e-mailbericht is ontvangen.

<u> Verwachte resultaten </u>:

De e-mail met beloningspunten die is bijgewerkt, had moeten zijn verzonden door de e-mailafzender die is geconfigureerd voor het tweede websitebereik.

<u> Ware resultaten </u>:

De e-mail met bonuspunten is verzonden door de e-mailafzender die is geconfigureerd voor het standaardbereik van de website.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
