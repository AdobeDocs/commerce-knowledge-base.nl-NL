---
title: 'ACSD-48234: onjuiste aantal categorieën van zoekresultaten in catalogus wanneer [!UICONTROL Display Out of Stock Products] enabled'
description: Pas de ACSD-48234-patch toe om het Adobe Commerce-probleem op te lossen waarbij het zoekresultaat van de catalogus een onjuist aantal categorieën van items bevat wanneer de [!UICONTROL Display Out of Stock Products] is ingeschakeld.
exl-id: 8e70fe73-d550-4e11-b25e-84955e136d12
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-48234: zoekresultaten in catalogus tonen onjuist aantal rubrieken **[!UICONTROL Display Out of Stock Products]** enabled

Met de ACSD-48234-patch wordt het probleem opgelost waarbij uit het zoekresultaat van de catalogus een onjuist aantal categorieën van items naar voren komt wanneer de **[!UICONTROL Display Out of Stock Products]** is ingeschakeld. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 is geïnstalleerd. De patch-id is ACSD-48234. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.


## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**
* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**
* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het resultaat van de cataloguszoekopdracht geeft een onjuist aantal rubrieken weer wanneer de **[!UICONTROL Display Out of Stock Products]** is ingeschakeld.

<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** en open **[!UICONTROL color]** kenmerk.
1. Voeg twee opties toe, bijvoorbeeld oranje en groen. Sla het kenmerk op.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** en voeg de **[!UICONTROL color]** aan de **[!UICONTROL Default]** kenmerkset.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** en instellen **[!UICONTROL Display Out of Stock Products]** tot _Ja_.
1. Categorie &#39;cat1&#39; maken.
1. Twee producten maken:
   1. Naam: prod1, Color: orange, Categorieën: cat1.
   1. Naam: prod2, Color: green, Categories: cat1.
1. Open de categorie kat1 op de winkel.
1. Selecteer de oranje kleur bij de gelaagde navigatie.

<u>Verwachte resultaten</u>:

Alleen product prod1 wordt weergegeven.

<u>Werkelijke resultaten</u>:

Zowel prod1 als prod2 producten worden getoond.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
