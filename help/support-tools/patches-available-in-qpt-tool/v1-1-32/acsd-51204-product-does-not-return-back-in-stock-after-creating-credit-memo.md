---
title: "ACSD-51204: Het product keert na het aanmaken van de kredietmemo niet terug in voorraad."
description: Pas de ACSD-51204-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het product na het maken van de creditmemo niet opnieuw in voorraad wordt genomen.
feature: Orders, Products, Returns
role: Admin
exl-id: 302033bc-2ca5-40d6-b692-24ae46b21c31
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-51204: Het product retourneert na het aanmaken van de kredietmemo niet meer in voorraad

De ACSD-51204-patch verhelpt het probleem waarbij het product na het maken van de creditmemo niet opnieuw in voorraad terugkeert. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 is geïnstalleerd. De patch-id is ACSD-51204. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het uitgekozen product keert niet terug in voorraad na het aanmaken van de kredietmemo.

<u>Stappen om te reproduceren</u>:

1. Installeren **[!UICONTROL Adobe Commerce]** en de **[!UICONTROL Inventory Management Module]** standaard *bron* en *voorraad* alleen.
1. Voeg een **[!UICONTROL new product]** met een hoeveelheid van *10*.
1. Het product toewijzen aan de **[!UICONTROL default stock]**.
1. Voeg het product in de winkel toe aan de kar en plaats een bestelling voor een totale beschikbare hoeveelheid van 10.
1. In het beheerpaneel, produceer een *factuur* en *verzending* voor de bestelling.
1. Een **[!UICONTROL Credit Memo]** met de *terugkeer naar voorraad* Schakel het selectievakje in voor alle items.
1. De producten controleren **[!UICONTROL Salable Quantity]** in de Admin.

<u>Verwachte resultaten</u>:

De verkoopbare hoeveelheid van het product moet terugkeren naar *10*.

<u>Werkelijke resultaten</u>:

De verkoopbare hoeveelheid van het product blijft als *0*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) in de [!DNL Quality Patches Tool] hulplijn.
