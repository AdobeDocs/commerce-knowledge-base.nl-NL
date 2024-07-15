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

# ACSD-51497: Kan cataloguspagina niet sorteren door douanekenmerken van type *Dropdown*

ACSD-51497 herstelt de flard de kwestie waar een klant geen cataloguspagina door een douanekenmerk van het type *Dropdown* kan sorteren. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 is geïnstalleerd. De patch-id is ACSD-51497. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een klant kan een cataloguspagina niet sorteren door een douanekenmerk van het type *Dropdown*.

<u> Stappen om te reproduceren </u>

1. Maak ongeveer zes eenvoudige producten en wijs deze toe aan één categorie.
1. Maak een productkenmerk om het als sorteeroptie toe te voegen aan de aanbiedingspagina&#39;s.

   * Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Add New Attribute]** .
   * Stel op het tabblad **[!UICONTROL Properties]** het volgende in:

      * *[!UICONTROL Default Label]* = *test*
      * *[!UICONTROL Catalog Input Type]* voor de Eigenaar van de Opslag = *Dropdown*
      * *[!UICONTROL Options]*:

         * *eerst*
         * *tweede*
         * *derde*
         * *vierde*

   * Stel op het tabblad **[!UICONTROL Storefront Properties]** het volgende in:

      * *[!UICONTROL Used for sorting in product listing]* = *ja*
      * Verlaat alle andere opties als *Gebrek*.

1. Wijs het *test* attribuut aan *Standaard* attributen toe die in **[!UICONTROL Admin]** worden geplaatst > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Vorm de producten om *test* attributenwaarden te hebben.

   * SKU: s00001, test: vierde
   * SKU: s00002, test: derde
   * SKU: s00003, test: tweede
   * SKU: s00004, test: eerste
   * SKU: s00005, test: vierde
   * SKU: s00006, test: derde

1. Cache opnieuw indexeren en wissen.
1. Ga naar de categorie op de winkelpagina.
1. De soort door het *test* attribuut.

<u> Verwachte resultaten </u>:

De producten worden gesorteerd door het *test* attribuut.

<u> Ware resultaten </u>:

De producten worden niet gesorteerd door het *test* attribuut.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
