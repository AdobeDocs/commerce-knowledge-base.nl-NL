---
title: '''ACSD-48366: productafbeelding niet weergegeven op [!UICONTROL Back to Stock] e-mailsjabloon'
description: Pas de ACSD-48366-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de miniatuurafbeelding van het product niet wordt weergegeven in de voorraadwaarschuwingsmail van het product.
exl-id: 57b549b0-6e97-4d5f-927e-9585f3257872
feature: Admin Workspace, Communications, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-48366: productafbeelding niet weergegeven op [!UICONTROL Back to Stock] e-mailsjabloon

De ACSD-48366-patch verhelpt het probleem dat de miniatuurafbeelding van het product niet wordt weergegeven in het bericht voor voorraadwaarschuwingen van het product. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 is geïnstalleerd. De patch-id is ACSD-48366. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De afbeelding van het product wordt niet weergegeven op het tabblad [!UICONTROL Back to Stock] e-mailsjabloon.

<u>Stappen om te reproduceren</u>:

1. Inschakelen *[!UICONTROL Product Alert]* for *[!UICONTROL Back in Stock]* door naar **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]** > **[!UICONTROL Allow Alert When Product Comes Back in Stock]** = *[!UICONTROL Yes]*.
1. Inschakelen *[!UICONTROL Display Out of Stock Products]* door naar **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Display Out of Stock]** = *[!UICONTROL Yes]*.
1. Maak een eenvoudig product met qty = 0.
1. Maak een klant van de winkel en meld u aan voor het bovenstaande product om productwaarschuwingen te ontvangen wanneer het product in voorraad is.
1. Maak het product in voorraad.
1. Voer de waarschuwing voor het product uit.

   ```
   n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Start de productwaarschuwing voor de klant.

   ```
   bin/magento queue:consumers:start product_alert
   ```

1. Controleer het e-mailbericht. Het e-mailbericht met voorraadwaarschuwingen moet nu beschikbaar zijn in de e-mailcatcher.

<u>Verwachte resultaten</u>:

De afbeelding van het product wordt weergegeven in het bericht voor voorraadwaarschuwing.

<u>Werkelijke resultaten</u>:

De afbeelding van het product is niet beschikbaar in het bericht voor voorraadwaarschuwingen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
