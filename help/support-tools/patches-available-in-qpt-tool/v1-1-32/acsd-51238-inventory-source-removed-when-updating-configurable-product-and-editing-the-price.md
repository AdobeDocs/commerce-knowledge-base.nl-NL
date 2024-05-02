---
title: "ACSD-51238: inventarisbron wordt verwijderd wanneer een configureerbaar product wordt bijgewerkt en de prijs wordt bewerkt"
description: Pas de ACSD-51238-patch toe om het Adobe Commerce-probleem op te lossen waarbij de inventarisbron wordt verwijderd tijdens het bijwerken van een configureerbaar product en het bewerken van de prijs.
exl-id: ab2f60fd-5da3-45f7-a489-6f4f9d34e1f1
feature: Configuration, Inventory, Orders, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51238: de inventarisbron wordt verwijderd wanneer een configureerbaar product wordt bijgewerkt en de prijs wordt bewerkt

De ACSD-51238-patch verhelpt het probleem waarbij de inventarisbron wordt verwijderd bij het bijwerken van een configureerbaar product en het bewerken van de prijs. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.32 is geïnstalleerd. De patch-id is ACSD-51238. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De inventarisbron wordt verwijderd wanneer u een configureerbaar product bijwerkt en de prijs bewerkt.

<u>Stappen om te reproduceren</u>:

1. Installeren **[!DNL Adobe Commerce]** with **[!DNL Inventory module]**
1. Ga naar de **[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]** en maken *twee bronnen* en *twee bestanden*.
1. Een **[!UICONTROL configurable product]** en toewijzen aan **[!UICONTROL default sources]** of **[!UICONTROL newly created sources]**.
1. Klik op de knop **[!UICONTROL next button]** en *opslaan* het product.
1. Bewerk nu hetzelfde **[!UICONTROL Configurable Product]** en klik op **[!UICONTROL Edit Configuration]** in de **[!UICONTROL Configuration tab]**.
1. In `Step 3: Bulk Images,Price and Quantity`wijzigt u de `price` en vertrekken `Quantity` en `Images` tot `Skip quantity at this time` en `Skip image uploading at this time` respectievelijk.
1. Klikken op **[!UICONTROL next button]** en het product te genereren.

<u>Verwachte resultaten</u>

De hoeveelheid per bron in de **[!UICONTROL Configuration tab]** mag niet leeg zijn.

<u>Werkelijke resultaten</u>

De hoeveelheid per bron in de **[!UICONTROL Configuration tab]** is leeg.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) in de [!DNL Quality Patches Tool] hulplijn.
