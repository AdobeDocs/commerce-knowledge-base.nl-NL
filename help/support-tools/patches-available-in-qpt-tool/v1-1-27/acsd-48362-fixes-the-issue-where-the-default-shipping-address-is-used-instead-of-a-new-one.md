---
title: 'ACSD-48362: het standaardverzendadres wordt gebruikt in plaats van een nieuw adres.'
description: Pas de ACSD-48362-patch toe om het Adobe Commerce-probleem op te lossen waarbij het standaardverzendadres wordt gebruikt in plaats van een nieuw adres wanneer u een order plaatst met behulp van een verhandelbaar aanhalingsteken.
exl-id: 52f518b6-6f73-42cc-ac1b-c893cd5007fa
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-48362: het standaardverzendadres wordt gebruikt in plaats van een nieuw adres

De ACSD-48362-patch verhelpt het probleem waarbij het standaardverzendadres wordt gebruikt in plaats van het zojuist toegevoegde adres wanneer een bestelling wordt geplaatst met behulp van een verhandelbaar aanhalingsteken. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 is geïnstalleerd. De patch-id is ACSD-48362. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het standaardverzendadres wordt gebruikt in plaats van het zojuist toegevoegde verzendadres wanneer u een bestelling plaatst met behulp van een verhandelbaar aanhalingsteken.

<u>Stappen om te reproduceren</u>:

1. B2B-aanhalingsteken inschakelen door naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]**.
1. Meld u aan als gebruiker van het bedrijf.
1. Voeg een product toe aan de kar.
1. Ga naar de winkelwagentje pagina en vraag een prijsopgave.
1. Ga naar de **[!UICONTROL My Quotes]** en selecteer het citaat dat enkel werd gecreeerd.
1. Ga naar de **[!UICONTROL Shipping Information]** van de prijsopgave van de klant.
   * Klikken **[!UICONTROL Add New Address]**, vult het formulier in en slaat het adres op (selecteer niet **[!UICONTROL Use as my default billing address]** of **[!UICONTROL Use as my default shipping address]**).
1. Klikken **[!UICONTROL Send for Review]** op de prijsopgave van de klant.
1. Ga naar Adobe Commerce Admin als beheerder gebruiker, open de citaat die enkel werd gecreeerd en klik **[!UICONTROL Send]**.
1. Ga nu naar de prijsopgave van de klant, vernieuw de pagina en klik op **[!UICONTROL Proceed to Checkout]**.
1. Op de afhandelingspagina wordt het standaardverzendadres weergegeven, zelfs als het nieuwe verzendadres is geselecteerd.
1. Klikken **[!UICONTROL Continue]** en plaats de bestelling.

<u>Verwachte resultaten</u>:

De bestelling moet het nieuwe adres gebruiken zonder het standaardverzendadres op de afhandelingspagina opnieuw te selecteren.

<u>Werkelijke resultaten</u>:

De bestelling wordt geplaatst met het standaardverzendadres.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure. 

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
