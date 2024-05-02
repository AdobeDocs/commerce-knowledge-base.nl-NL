---
title: '''ACSD-52606: Foutbericht dat wordt weergegeven wanneer de gebruiker klikt op ''De bestelling op de hoogte stellen is klaar voor afhalen'''''
description: Pas de ACSD-52606-patch toe om het Adobe Commerce-probleem op te lossen waarbij een foutbericht wordt weergegeven wanneer de gebruiker op ** klikt[!UICONTROL Notify Order is Ready for Pickup]**.
feature: Orders, User Account
role: Admin, Developer
exl-id: c3e69eb1-90bf-46cf-9b53-110e40e0c3c1
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-52606: Foutbericht dat wordt weergegeven wanneer de gebruiker klikt op &quot;De bestelling op de hoogte stellen is klaar voor ophaalbewerking&quot;

De ACSD-52606-patch verhelpt het probleem waarbij een foutbericht verschijnt *Uw bestelling kan niet worden opgehaald* wordt weergegeven wanneer de gebruiker klikt **[!UICONTROL Notify Order is Ready for Pickup]**. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.37 is geïnstalleerd. De patch-id is ACSD-52606. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een foutbericht *Uw bestelling kan niet worden opgehaald* wordt weergegeven op het scherm wanneer de gebruiker klikt **[!UICONTROL Notify Order is Ready for Pickup]**.

<u>Vereisten</u>:

De inventarismodules worden geïnstalleerd.

<u>Stappen om te reproduceren</u>:

1. Nieuwe instantie installeren.
1. Maak een nieuwe bron en voorraad.
1. Wijs de nieuwe bron toe aan de standaardwebsite.
1. Ophaallocatie inschakelen voor de nieuwe bron.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** en **[!UICONTROL In-Store Delivery]**.
1. Een *In voorraad* eenvoudig product met *QTY=0* voor alle voorraden en *[!UICONTROL Manage Stock = No]* en deze aan beide bronnen toewijzen.
1. Maak een bestelling van de voorzijde met het product dat u in de vorige stap hebt gemaakt en kies *[!UICONTROL In-Store Pickup]* als de leveringsmethode.
1. Ga in Beheer naar **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice that order]**.
1. Klik op **[!UICONTROL Notify order is ready for pickup]**.

<u>Verwachte resultaten</u>:

U krijgt een melding zonder fouten.

<u>Werkelijke resultaten</u>:

U krijgt het volgende foutbericht: *Uw bestelling kan niet worden opgehaald*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
