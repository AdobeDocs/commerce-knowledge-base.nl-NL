---
title: 'ACSD-54319: De prijs van het product toont nul in *[!UICONTROL Products in Carts]* rapport'
description: Pas de ACSD-54319-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de productprijs nul weergeeft in *[!UICONTROL Products in Carts]*-rapport
feature: Reporting, Products
role: Admin, Developer
exl-id: f53b3ed3-d5d5-461c-bba2-4f9f3f038580
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-54319: Productprijs geeft nul weer in *[!UICONTROL Products in Carts]* -rapport

De ACSD-54319-patch verhelpt het probleem waarbij de prijs van het product nul weergeeft in het *[!UICONTROL Products in Carts]* -rapport. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 wordt geïnstalleerd. De patch-id is ACSD-54319. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prijs van het product wordt nul weergegeven in het rapport *[!UICONTROL Products in Carts]* .

<u> Stappen om </u> te reproduceren:

1. Stel **[!UICONTROL Catalog Price Scope]** in op **[!UICONTROL Website]** via **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]** .
1. Maak een tweede website via **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** .
1. Maak een product van **[!UICONTROL Catalog]** > **[!UICONTROL Products]** .
1. Wijs dit product alleen toe aan de tweede website.
1. Voeg een product vanaf de tweede website toe aan het winkelwagentje.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Marketing]** > **[!UICONTROL Products In Carts]** raster.
1. Controleer de *[!UICONTROL Price]* -kolom in het *[!UICONTROL Products In Carts]* -raster.

<u> Verwachte resultaten </u>:

Productprijs is niet nul in het rapportraster van *[!UICONTROL Products in Carts]* .

<u> Ware resultaten </u>:

Productprijs is nul in het rapportraster van *[!UICONTROL Products in Carts]* .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
