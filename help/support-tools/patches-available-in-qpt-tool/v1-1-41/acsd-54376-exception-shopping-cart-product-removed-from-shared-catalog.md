---
title: '"ACSD-54376: Uitzondering in winkelwagentje wanneer het product uit het winkelwagentje wordt verwijderd [!UICONTROL shared catalog]'''
description: Pas de ACSD-54376-patch toe om het Adobe Commerce-probleem op te lossen waarbij een uitzondering optreedt in het winkelwagentje wanneer een product uit het winkelwagentje wordt verwijderd [!UICONTROL shared catalog] nadat het aan de kar is toegevoegd.
feature: Shopping Cart, B2B
role: Admin, Developer
exl-id: a1e5c084-532f-49e8-ab87-6674b44218e8
source-git-commit: 1cc565d5888e5a380c04879d9aced2c19e92c2e5
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-54376: Uitzondering in winkelwagentje wanneer het product wordt verwijderd [!UICONTROL shared catalog]

De ACSD-54376-patch verhelpt het probleem waarbij een uitzondering optreedt in het winkelwagentje wanneer een product uit het winkelwagentje wordt verwijderd [!UICONTROL shared catalog] nadat het aan de kar is toegevoegd. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 is geïnstalleerd. De patch-id is ACSD-54376. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treedt een uitzondering op in het winkelwagentje wanneer een product uit het winkelwagentje wordt verwijderd [!UICONTROL shared catalog] nadat het aan de kar is toegevoegd.

<u>Stappen om te reproduceren</u>:

1. Adobe Commerce installeren met B2B.
1. Inschakelen [!UICONTROL shared catalog].
1. Een product maken en toewijzen aan de standaardversie [!UICONTROL shared catalog].
1. Voeg een product uit de winkel toe aan de winkelwagentje.
1. Het product uit de [!UICONTROL shared catalog].
1. Navigeer naar de uitcheckpagina met behulp van de mini-cart vervolgkeuzelijst.

<u>Verwachte resultaten</u>:

Uitzonderingen worden afgehandeld en niet aan u weergegeven.

<u>Werkelijke resultaten</u>:

Een niet-afgehandelde uitzondering wordt weergegeven op de uitcheckpagina.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
