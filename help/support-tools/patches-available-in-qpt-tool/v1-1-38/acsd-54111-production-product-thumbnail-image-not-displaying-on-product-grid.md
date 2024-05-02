---
title: 'ACSD-54111: Afbeelding met productminiaturen wordt niet weergegeven'
description: Pas de ACSD-54111-patch toe om het Adobe Commerce-probleem op te lossen, waarbij alle afbeeldingen worden vervangen door de standaardvoorlopige afbeelding van het product.
feature: Products
role: Admin, Developer
exl-id: 087786e3-9d61-4fef-8884-8d22fa9170e3
source-git-commit: a863015920917050106ed5d210d0511515807cc7
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-54111: Afbeelding met productminiatuur wordt niet weergegeven

Met de ACSD-54111-patch is het probleem verholpen waarbij alle afbeeldingen worden vervangen door de standaardvoorlopige afbeelding van het product. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 is geïnstalleerd. De patch-id is ACSD-5411. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden): 2.4.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden): 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De miniatuurafbeelding van het product wordt niet weergegeven.

<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]** > **[!UICONTROL Edit Theme]** > **[!UICONTROL Product Image Watermarks]** > **[!UICONTROL Thumbnail]**.
1. Upload de afbeelding met een miniatuur en stel de afbeeldingspositie in als *[!UICONTROL Center]*.
1. Klikken op **[!UICONTROL Save Configuration]**.
1. Cache wissen.
1. Ga naar de winkel als gast/klant.
1. Voeg een product toe aan de kar.
1. Uitvoeren `bin/magento catalog:image:resize` vanuit de console.
1. Open de miniwinkelwagentje op de voorkant of het productraster op de achtergrond om te zien of de miniaturen van de afbeelding zichtbaar zijn.

<u>Verwachte resultaten</u>:

Productafbeeldingen worden niet vervangen door de voorlopige afbeelding.

<u>Werkelijke resultaten</u>:

Afbeeldingen van producten worden vervangen door de standaardafbeelding van de tijdelijke aanduiding voor het product.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
