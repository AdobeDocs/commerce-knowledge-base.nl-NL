---
title: '"ACSD-47076: [!DNL Vimeo] video''s kunnen niet worden afgespeeld op de storefront.'''
description: Pas de ACSD-47076-patch toe om het Adobe Commerce-probleem op te lossen, waarbij [!DNL Vimeo] video's kunnen niet worden afgespeeld op de winkelserver.
exl-id: 52161c0d-3d51-45a3-ba41-36f955df0bea
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-47076: [!DNL Vimeo] video&#39;s kunnen niet worden afgespeeld op de winkelachtergrond

De ACSD-47076-patch verhelpt het probleem waarbij: [!DNL Vimeo] video&#39;s kunnen niet worden afgespeeld op de winkelserver. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 is geïnstalleerd. De patch-id is ACSD-47076. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.3-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!DNL Vimeo] video&#39;s kunnen niet worden afgespeeld op de winkelserver.

<u>Stappen om te reproduceren</u>:

1. Voeg een [!DNL Vimeo] video naar een product in de Commerce [!UICONTROL Admin] > **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > Productbewerkingspagina > **[!UICONTROL Images and Videos]**.
1. Open het product op de winkel en speel de video af.

<u>Verwachte resultaten</u>:

De [!DNL Vimeo] video kan worden afgespeeld.

<u>Werkelijke resultaten</u>:

De [!DNL Vimeo] video kan niet op de storefront worden afgespeeld.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
