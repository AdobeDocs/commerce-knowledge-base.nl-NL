---
title: 'ACSD-50814: Admin user not able to create credit memo'
description: Pas de ACSD-50814-patch toe om het Adobe Commerce-probleem op te lossen waarbij een beheerder geen creditmemo kan maken.
exl-id: bda374cf-6fb7-479f-8130-213ce3cc553e
feature: Admin Workspace, Orders, Returns
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-50814: Admin-gebruiker kan geen creditmemo maken

De ACSD-50814-patch verhelpt het probleem waarbij een beheerder geen creditmemo kan maken. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 is geïnstalleerd. De patch-id is ACSD-50814. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een beheerder kan geen creditnota maken.

<u>Stappen om te reproduceren</u>:

1. Navigeer in Adobe Commerce Admin naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping methods]** > **[!UICONTROL Free shipping]** en instellen **[!UICONTROL Enable free shipping]** tot *[!UICONTROL Yes]*
1. Opnieuw Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** Vouw de berekeningsinstellingen uit en stel deze in:
   * [!UICONTROL Shipping prices] = [!UICONTROL Including tax]
   * [!UICONTROL Enable cross border trade] = [!UICONTROL No]
1. De weergave-instellingen voor prijzen uitbreiden en de [!UICONTROL Display shipping prices] = [!UICONTROL Including tax].
1. Uitbreiden [!UICONTROL Orders], [!UICONTROL Invoices], [!UICONTROL Credit memo] weergave-instellingen en set [!UICONTROL Display shipping amount] = [!UICONTROL Including tax].
1. caches wissen.
1. Plaats een bestelling op de winkel.
1. Maak een factuur voor de bestelling in de beheerder.
1. Maak een creditmemo.

<u>Verwachte resultaten</u>:

De creditmemo wordt gemaakt.

<u>Werkelijke resultaten</u>:

De volgende fout wordt gegenereerd:

*De pagina kan niet worden weergegeven vanwege de fout*

```
report.CRITICAL: DivisionByZeroError: Division by zero in vendor/magento/module-sales/Model/Order/Creditmemo/Total/Tax.php:139*
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
