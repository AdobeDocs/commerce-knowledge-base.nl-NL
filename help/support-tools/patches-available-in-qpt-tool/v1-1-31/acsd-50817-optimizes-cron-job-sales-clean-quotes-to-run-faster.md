---
title: 'ACSD-50817: Optimizes cron job sales_clean_quotes to run rapid'
description: Pas ACSD-50817 flard toe om de cron baan ` sales_clean_quotes' te optimaliseren om sneller te lopen door een samengestelde index op ` store_id ` en ` update_at' kolommen in de citaatlijst toe te voegen.
exl-id: b08b12ff-37ac-4a7d-bce2-2a27e4f916f0
feature: Quotes
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-50817: Hiermee wordt de snijtaak geoptimaliseerd `sales_clean_quotes` sneller werken

De ACSD-50817-patch optimaliseert de snijtaak `sales_clean_quotes` om sneller te werken door een samengestelde index toe te voegen op de `store_id` en `updated_at` kolommen in de citaatlijst. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.31 is geïnstalleerd. De patch-id is ACSD-50817.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De uitsnijdtaak `sales_clean_quotes` is te langzaam. Met deze patch is de patch geoptimaliseerd om sneller te worden uitgevoerd door een samengestelde index toe te voegen op de `store_id` en `updated_at` kolommen in de citaatlijst.

<u>Stappen om te reproduceren</u>:

1. 50-80 MB aanhalingstekens genereren met `updated_at` ingesteld op een periode van &lt; 30 dagen.
1. De uitsnijdtaak uitvoeren `sales_clean_quotes` of de volgende vraag op de citaatlijst:

   ```cron
   SELECT COUNT(*) FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0')
   
   SELECT * FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0') LIMIT 50
   ```

<u>Verwachte resultaten</u>

Uitsnijdtaak `sales_clean_quotes` is geoptimaliseerd om sneller te worden uitgevoerd door een samengestelde index toe te voegen aan de `store_id` en `updated_at` kolommen in de citaatlijst.

<u>Werkelijke resultaten</u>

De query is te langzaam.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
