---
title: '''ACSD-47666: zoeken in [!UICONTROL User Roles] werkt niet"'
description: Pas de ACSD-47666-patch toe om het Adobe Commerce-probleem op te lossen waarbij het filter werkt op [!UICONTROL User Roles] werkt niet zoals verwacht.
exl-id: c1b6d3ab-e132-4b09-8692-2b82f9ca6864
feature: Roles/Permissions, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# ACSD-47666: zoekopdracht in **[!UICONTROL User Roles]** werkt niet

De ACSD-47666-patch lost het probleem op waar de zoekopdracht in **[!UICONTROL User Roles]** werkt niet. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 is geïnstalleerd. De patch-id is ACSD-4766. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De filterfunctie op **[!UICONTROL User Roles]** werkt niet zoals verwacht.

<u>Stappen om te reproduceren</u>:

1. Aanmelden bij Adobe Commerce Admin > **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**.
1. Open een bestaande rol in de lijst.
1. Open de **[!UICONTROL Role Users]** tab.
1. Typ een query in een kolom.
1. Druk op Enter.

<u>Verwachte resultaten</u>:

De **[!UICONTROL User Roles]** filterfunctie moet resultaten filteren op basis van de query.

<u>Werkelijke resultaten</u>:

Oneindig laden met consolefout _(index):9 Uncaught TypeError: Cannot read properties of null (reading &#39;down&#39;)_.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie. 

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
