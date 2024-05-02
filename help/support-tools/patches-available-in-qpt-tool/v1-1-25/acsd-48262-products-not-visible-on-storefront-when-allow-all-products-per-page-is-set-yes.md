---
title: '"ACSD-48262: producten die niet zichtbaar zijn in de winkel wanneer [!UICONTROL Allow All Products Per Page] is ingesteld [!UICONTROL Yes]'''
description: Pas de ACSD-48262-patch toe om het Adobe Commerce-probleem op te lossen, waarbij producten niet zichtbaar zijn op de winkel wanneer de [!UICONTROL Allow All Products Per Page] instellen op [!UICONTROL Yes].
exl-id: 327cad03-441d-4adb-8a10-802f06d3fcd1
feature: Admin Workspace, Cache, Categories, Orders, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-48262: producten die niet zichtbaar zijn in de winkel wanneer [!UICONTROL Allow All Products Per Page] is ingesteld *[!UICONTROL Yes]*

De ACSD-48262-patch verhelpt het probleem dat producten niet zichtbaar zijn op de winkel als de [!UICONTROL Allow All Products Per Page] instellen op *[!UICONTROL Yes]*. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 is geïnstalleerd. De patch-id is ACSD-48262. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De ACSD-48262-patch verhelpt het probleem dat producten niet zichtbaar zijn op de winkel als de [!UICONTROL Allow All Products Per Page] instellen op *[!UICONTROL Yes]*.

<u>Stappen om te reproduceren</u>:

1. Maak een testcategorie.
1. Maak een testproduct in de testcategorie.
1. Blader naar de pagina met productcategorieën op de winkel en controleer of het product zichtbaar is.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** en stelt de [!UICONTROL Allow All Products Per Page] instellen op *[!UICONTROL Yes]*.
1. Cache wissen.
1. Categoriepagina controleren in de winkel.

<u>Verwachte resultaten</u>:

Het product is zichtbaar.

<u>Werkelijke resultaten</u>:

Het product is niet zichtbaar.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
