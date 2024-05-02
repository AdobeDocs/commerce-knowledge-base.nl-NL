---
title: "ACSD-51265: Herindexering voor gebundelde producten optimaliseren"
description: Pas de ACSD-51265-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de 'catalog_product_price' rendexing-prestaties laag zijn wanneer het systeem te veel gebundelde producten bevat.
feature: Products, Price Indexer
role: Admin
exl-id: ddf23c19-b1ed-4064-adbc-58707eb63cc9
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-51265: Herindexering optimaliseren voor gebundelde producten

De ACSD-51265-patch verhelpt het probleem waarbij de `catalog_product_price` de prestaties van het systeem zijn laag wanneer het systeem te veel gebundelde producten bevat . Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.35 is geïnstalleerd. De patch-id is ACSD-51265. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prijs van het catalogusproduct die opnieuw indexeert is laag wanneer er teveel gebundelde producten in het systeem zijn.

<u>Stappen om te reproduceren</u>:

1. Een catalogus genereren met ten minste *10 000* gebundelde producten met dynamische prijsopties.
1. Reïndex van de productprijs uitvoeren.

<u>Verwachte resultaten</u>

Het opnieuw indexeren van de productprijs duurt minder dan 15 minuten.

<u>Werkelijke resultaten</u>

Het opnieuw berekenen van de productprijs duurt langer dan een uur.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
