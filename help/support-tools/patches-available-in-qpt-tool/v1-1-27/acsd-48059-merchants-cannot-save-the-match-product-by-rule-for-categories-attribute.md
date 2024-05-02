---
title: 'ACSD-48059: handelaren kunnen niet opslaan [!UICONTROL Match product by rule] for Categories attribute.'
description: Pas de ACSD-48059-patch toe om het Adobe Commerce-probleem op te lossen, waarbij handelaren het [!UICONTROL Match product by rule] voor het kenmerk Categorieën.
exl-id: 97213157-1b54-4634-9c76-c9ab8fa96e17
feature: Admin Workspace, Attributes, Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-48059: Merchants kunnen de *[!UICONTROL Match product by rule]* voor de categorie

De ACSD-48059-patch verhelpt het probleem waarbij handelaren de *[!UICONTROL Match product by rule]* voor het kenmerk Categorieën in [!DNL Visual Merchandiser]. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27 is geïnstalleerd. De patch-id is ACSD-48059. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) >=2.3.7 &lt;2.4.7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Handelaren kunnen de *[!UICONTROL Match product by rule]* voor categorieën, kenmerk in [!DNL Visual Merchandiser].

<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Visual Merchandiser]** > **[!UICONTROL Visible Attributes for Category Rules]**, voegt categorieën toe.
1. Ga naar Adobe Commerce Admin > **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
   * Ga naar de [!UICONTROL Products in Category] sectie.
   * Een nieuwe toevoegen *[!UICONTROL Match products by rule]* voorwaarde met het categoriekenmerk.

<u>Verwachte resultaten</u>:

De categorie is opgeslagen.

<u>Werkelijke resultaten</u>:

* U kunt de categorie niet opslaan met de nieuwe regel en voorwaarde.
* *Er is iets misgegaan tijdens het opslaan van de categorie* Er wordt een fout weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
