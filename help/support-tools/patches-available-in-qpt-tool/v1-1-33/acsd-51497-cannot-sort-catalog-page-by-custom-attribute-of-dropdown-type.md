---
title: 'ACSD-51497: Kan cataloguspagina niet sorteren op aangepast kenmerk van het type Dropdown'
description: Pas de ACSD-51497-patch toe om het Adobe Commerce-probleem op te lossen waarbij een klant een cataloguspagina niet kan sorteren op aangepast kenmerk van het type Dropdown.
feature: Attributes, Cache, Catalog Management, Categories
role: Developer
exl-id: 60a4f375-9b9a-4026-9dc7-d9f847a75656
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-51497: Kan cataloguspagina niet sorteren op aangepast kenmerk van type *Vervolgkeuzelijst*

De ACSD-51497-patch verhelpt het probleem waarbij een klant een cataloguspagina niet kan sorteren op een aangepast kenmerk van het type *Vervolgkeuzelijst*. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 is geïnstalleerd. De patch-id is ACSD-51497. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een klant kan een cataloguspagina niet sorteren op een aangepast kenmerk van het type *Vervolgkeuzelijst*.

<u>Stappen om te reproduceren</u>

1. Maak ongeveer zes eenvoudige producten en wijs deze toe aan één categorie.
1. Maak een productkenmerk om het als sorteeroptie toe te voegen aan de aanbiedingspagina&#39;s.

   * Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Add New Attribute]**.
   * In de **[!UICONTROL Properties]** , stelt u het volgende in:

      * *[!UICONTROL Default Label]* = *test*
      * *[!UICONTROL Catalog Input Type]* voor Winkeleigenaar = *Vervolgkeuzelijst*
      * *[!UICONTROL Options]*:

         * *first*
         * *seconde*
         * *derde*
         * *vierde*

   * In de **[!UICONTROL Storefront Properties]** , stelt u het volgende in:

      * *[!UICONTROL Used for sorting in product listing]* = *Ja*
      * Alle andere opties behouden als *Standaard*.

1. Wijs het *test* aan de *Standaard* kenmerkset in **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Vorm de producten om te hebben *test* kenmerkwaarden.

   * SKU: s00001, test: vierde
   * SKU: s00002, test: derde
   * SKU: s00003, test: tweede
   * SKU: s00004, test: eerste
   * SKU: s00005, test: vierde
   * SKU: s00006, test: derde

1. Cache opnieuw indexeren en wissen.
1. Ga naar de categorie op de winkelpagina.
1. Sorteren op *test* kenmerk.

<u>Verwachte resultaten</u>:

De producten worden door de *test* kenmerk.

<u>Werkelijke resultaten</u>:

De producten worden niet gesorteerd door de *test* kenmerk.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
