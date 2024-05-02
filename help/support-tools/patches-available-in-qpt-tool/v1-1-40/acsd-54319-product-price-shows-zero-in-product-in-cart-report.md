---
title: "ACSD-54319: De prijs van het product is nul in *[!UICONTROL Products in Carts]* rapport "
description: Pas de ACSD-54319-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de prijs van het product nul is in *[!UICONTROL Products in Carts]* rapport
feature: Reporting, Products
role: Admin, Developer
exl-id: f53b3ed3-d5d5-461c-bba2-4f9f3f038580
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-54319: De prijs van het product is nul in *[!UICONTROL Products in Carts]* verslag

De ACSD-54319-patch verhelpt het probleem waarbij de prijs van het product nul is in *[!UICONTROL Products in Carts]* verslag. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 is geïnstalleerd. De patch-id is ACSD-54319. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De productprijs is nul in *[!UICONTROL Products in Carts]* verslag.

<u>Stappen om te reproduceren</u>:

1. Set **[!UICONTROL Catalog Price Scope]** tot **[!UICONTROL Website]** van **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]**.
1. Een tweede website maken van **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. Een product maken van **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Wijs dit product alleen toe aan de tweede website.
1. Voeg een product vanaf de tweede website toe aan het winkelwagentje.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Marketing]** > **[!UICONTROL Products In Carts]** raster.
1. Controleer de *[!UICONTROL Price]* kolom in *[!UICONTROL Products In Carts]* raster.

<u>Verwachte resultaten</u>:

De productprijs is niet nul in *[!UICONTROL Products in Carts]* rapportraster.

<u>Werkelijke resultaten</u>:

Productprijs is nul in *[!UICONTROL Products in Carts]* rapportraster.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
