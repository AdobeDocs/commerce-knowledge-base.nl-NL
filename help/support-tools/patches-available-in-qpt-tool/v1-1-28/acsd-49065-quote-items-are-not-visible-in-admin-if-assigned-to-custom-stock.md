---
title: 'ACSD-49065: Offertepunten zijn niet zichtbaar in admin'
description: Pas de ACSD-49065-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de aanhalingstekens niet zichtbaar zijn in de beheerder als ze alleen zijn toegewezen aan de aangepaste voorraad.
exl-id: 3a5ceb4c-4c94-4938-98d9-9171f2633056
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-49065: Offertepunten zijn niet zichtbaar in admin

De ACSD-49065-patch verhelpt het probleem waarbij de aanhalingstekens niet zichtbaar zijn in de beheerder als deze alleen zijn toegewezen aan de aangepaste voorraad. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 is geïnstalleerd. De patch-id is ACSD-49065. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De aanhalingstekens zijn niet zichtbaar in de beheerder als deze alleen zijn toegewezen aan de aangepaste voorraad.

Vereisten:

**[!UICONTROL B2B]** en **[!UICONTROL Inventory]** moeten worden geïnstalleerd.

<u>Stappen om te reproduceren</u>:

1. Inschakelen **[!UICONTROL Company]** en **[!UICONTROL B2B Quote]** krachtens **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Een secundair bestand maken **[!UICONTROL Inventory Source]** en deze aan een secundair **[!UICONTROL Inventory Stock]**.
1. Een nieuw product maken door alleen het secundaire (niet-standaard) toe te wijzen **[!UICONTROL Inventory Source]**.
1. Ga naar de winkel en maak een nieuw bedrijfsaccount. Aanmelden als de **[!UICONTROL Company Admin]** en voeg het gemaakte product toe aan de winkelwagentje.
1. Ga naar de winkelwagentje en *[!UICONTROL Request a Quote]*.
1. Ga naar de beheerder en bekijk het gevraagde citaat bij **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.

<u>Verwachte resultaten</u>:

De punten zijn zichtbaar in het nieuwe citaat dat met nieuwe producten wordt gecreeerd zonder de producten opnieuw te bewaren.

<u>Werkelijke resultaten</u>:

De *[!UICONTROL Items Quoted]* is leeg. Als u het nieuwe product opnieuw opslaat, worden de items weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
