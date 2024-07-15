---
title: '"ACSD-54890: ` aggregate_sales_report_bestsellers_data ` veroorzaakt  [!DNL MySQL]  fouten'''
description: Pas ACSD-54890 flard toe om de kwestie van Adobe Commerce te bevestigen waar ` aggregate_sales_report_bestsellers_data `  [!DNL MySQL]  fouten toe te schrijven aan `/tmpdisk ` die uit ruimte zijn veroorzaakt.
feature: Attributes
role: Admin, Developer
exl-id: 21a675dc-0750-4dc6-8cce-33e301f601bd
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# ACSD-54890: `aggregate_sales_report_bestsellers_data` veroorzaakt MySQL-fouten

De ACSD-54890-patch verhelpt het probleem waarbij `aggregate_sales_report_bestsellers_data` [!DNL MySQL] fouten veroorzaakt omdat `/tmpdisk` onvoldoende ruimte heeft. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 wordt geïnstalleerd. De patch-id is ACSD-54890. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

`aggregate_sales_report_bestsellers_data` veroorzaakt **[!DNL MySQL]** fouten omdat `/tmpdisk` onvoldoende ruimte heeft.

<u> Stappen om </u> te reproduceren:

Voer de `aggregate_sales_report_bestsellers_data` -snijtaak uit wanneer de `sales_bestsellers_aggregated_daily` -tabel een enorme hoeveelheid records heeft, zoals tientallen miljoenen records.

<u> Verwachte resultaten </u>:

Er treden geen fouten op.

<u> Ware resultaten </u>:

De volgende fout treedt op:
`report.ERROR: Cron Job aggregate_sales_report_bestsellers_data has an error: SQLSTATE[HY000]: General error: 3 Error writing file '/tmp/#sql/fd=72' (Errcode: 28 "No space left on device")`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
