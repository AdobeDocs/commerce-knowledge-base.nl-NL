---
title: 'ACSD-50817: optimaliseert verkoopmogelijkheden voor snijtaken_clean_quotes om sneller te werken'
description: Pas ACSD-50817 flard toe om de cron baan &grave; sales_clean_quotes' te optimaliseren om sneller te lopen door een samengestelde index op &grave; store_id &grave; en &grave; update_at' kolommen in de citaatlijst toe te voegen.
exl-id: b08b12ff-37ac-4a7d-bce2-2a27e4f916f0
feature: Quotes
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-50817: hiermee wordt de snijtaak `sales_clean_quotes` geoptimaliseerd en sneller uitgevoerd

De ACSD-50817-patch optimaliseert de uitsnijdtaak `sales_clean_quotes` zodat deze sneller wordt uitgevoerd door een samengestelde index toe te voegen aan de kolommen `store_id` en `updated_at` in de aanhalingstabel. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.31 wordt geïnstalleerd. De patch-id is ACSD-50817.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De uitsnijdtaak `sales_clean_quotes` is te langzaam. Met deze patch is deze geoptimaliseerd voor een snellere uitvoering door een samengestelde index toe te voegen aan de kolommen `store_id` en `updated_at` in de aanhalingstabel.

<u> Stappen om </u> te reproduceren:

1. Genereer 50-80 MB aanhalingstekens met `updated_at` ingesteld op een periode van &lt; 30 dagen.
1. Voer de uitsnijdtaak `sales_clean_quotes` of de volgende query op de aanhalingstabel uit:

   ```cron
   SELECT COUNT(*) FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0')
   
   SELECT * FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0') LIMIT 50
   ```

<u> Verwachte resultaten </u>

De uitsnijdtaak `sales_clean_quotes` wordt geoptimaliseerd om sneller te worden uitgevoerd door een samengestelde index toe te voegen aan de kolommen `store_id` en `updated_at` in de tabel met aanhalingstekens.

<u> Ware resultaten </u>

De query is te langzaam.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
