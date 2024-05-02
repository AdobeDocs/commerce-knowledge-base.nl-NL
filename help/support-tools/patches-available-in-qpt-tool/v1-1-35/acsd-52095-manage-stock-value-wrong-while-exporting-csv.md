---
title: 'ACSD-52095: De voorraadwaarde beheren is onjuist tijdens het exporteren van CSV'
description: Pas de ACSD-52095-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het product de voorraadwaarde beheert tijdens het exporteren van CSV.
feature: Inventory, Products
role: Admin, Developer
exl-id: 9e599931-e9b1-4216-b78d-3993d9c3132d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-52095: [!UICONTROL Manage Stock] waarde is onjuist tijdens exporteren van CSV

De ACSD-52095-patch verhelpt het probleem waarbij het product `manage_stock` waarde is onjuist tijdens het exporteren van CSV. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.35 is geïnstalleerd. De patch-id is ACSD-52095. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De `manage_stock` De waarde wordt na het exporteren van het product onjuist ingesteld op 0 in het CSV-bestand.

<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** en instellen **[!UICONTROL Manage Stock]** = *[!UICONTROL No]*.
1. Maak een nieuw product en sla dit op.
1. Ga naar **[!UICONTROL System]** > **[!UICONTROL Export]**.
1. Selecteren *[!UICONTROL Entity Type]* = *[!UICONTROL Products]* en de producten uitvoeren.
1. Controleer het gegenereerde CSV-bestand: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Opnieuw Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]**, en instellen  **[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]*.
1. Ga naar **Systeem** > **Exporteren**.
Selecteren *[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]*.
1. Controleer het gegenereerde CSV-bestand: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Open het product in Admin, ga naar **[!UICONTROL Advanced Inventory]** en de **[!UICONTROL Manage Stock]** waarde.

<u>Verwachte resultaten</u>

De **[!UICONTROL Manage Stock]** waarde is *1* wanneer deze voor de producten is ingeschakeld.

<u>Werkelijke resultaten</u>

De **[!UICONTROL Manage Stock]** waarde is *0* wanneer deze voor de producten is ingeschakeld.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) in de [!DNL Quality Patches Tool] hulplijn.
