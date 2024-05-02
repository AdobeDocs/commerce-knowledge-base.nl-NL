---
title: 'ACSD-53628: In het CSV-rapport met verkooporders worden onjuiste speciale tekens weergegeven'
description: Pas de ACSD-53628-patch toe om het Adobe Commerce-probleem op te lossen, waarbij in het CSV-rapport onjuiste speciale tekens worden weergegeven.
feature: Orders, Data Import/Export
role: Admin, Developer
exl-id: d898fdb8-cab9-49ab-ad8e-43feadf49aa0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-53628: In het CSV-rapport met verkooporders worden onjuiste speciale tekens weergegeven

De ACSD-53628-patch verhelpt het probleem waarbij in het CSV-rapport onjuiste speciale tekens worden weergegeven. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.37 is geïnstalleerd. De patch-id is ACSD-53628. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden): 2.4.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden): 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

In het CSV-rapport met verkooporders worden onjuiste speciale tekens weergegeven.

<u>Stappen om te reproduceren</u>:

1. Wijzigen **[!UICONTROL Base Currency]** en **[!UICONTROL Default Display Currency]** naar euro in de valutaopstelling.
1. Plaats een bestelling.
1. Ga op de zijbalk Beheerder naar **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Datums selecteren. Klik op **[!UICONTROL Show Report]**. Klikken **[!UICONTROL Export]** om de CSV te exporteren.

<u>Verwachte resultaten</u>:

Speciale tekens in een geëxporteerd CSV-bestand worden correct weergegeven in Excel.

<u>Werkelijke resultaten</u>:

In het CSV-rapport met verkooporders worden speciale tekens onjuist weergegeven.


## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
