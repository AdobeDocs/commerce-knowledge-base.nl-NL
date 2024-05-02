---
title: Bekende uitgave van Adobe Commerce 2.4.0 - Export Tax Rates werkt niet
description: Dit artikel biedt een oplossing voor een bekende Adobe Commerce 2.4.0-probleem waarbij de knop **Exportbelastingen** niet werkt.
exl-id: 29a34a1f-d23a-43cb-ac1f-8711ce25fa6c
feature: Data Import/Export, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Bekende uitgave van Adobe Commerce 2.4.0 - Export Tax Rates werkt niet

Dit artikel biedt een oplossing voor een bekende Adobe Commerce 2.4.0-probleem waarbij de **Belastingtarieven voor uitvoer** werkt niet.

## Betrokken producten en versies

* Adobe Commerce over cloudinfrastructuur 2.4.0
* Adobe Commerce op locatie 2.4.0

## Probleem

<u>Stappen om te reproduceren:</u>

1. Ga naar het deelvenster Commerce Admin > **Winkels** > **Belastingregels**.
1. Klik op de knop **Nieuwe belastingregel toevoegen** knop.
1. Klik op de tekst van de **Belastingtarieven voor uitvoer** knop.

   ![magento_export_tax_rates.png](assets/mceclip0.png)

<u>Verwacht resultaat</u>:

A `tax_rates.csv` bestanden downloaden met belastingtarieven.

<u>Werkelijk resultaat</u>:

Er wordt geen CSV-bestand gedownload.

## Oplossing

Oplossing:

Klik op de linkeronderrand van het dialoogvenster **Belastingtarieven voor uitvoer** om de `tax_rates.csv` bestand.

![magento_export_tax_rates.png](assets/mceclip1.png)

Het probleem wordt opgelost in een 2.4.1-patch.

## Gerelateerde lezing

In onze kennisbasis voor ondersteuning:

* [Bekende uitgave van Adobe Commerce 2.4.0: Betalingsmethoden voor Braintree worden niet weergegeven bij de afhandeling van meerdere adressen](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md).
* [Aanmaak van verzendlabels Bekend probleem in Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md).
* [Bekende uitgave van Adobe Commerce 2.4.0 - Vernieuwen van de activiteiten van de Klant werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md).
* [Bekende uitgave van Adobe Commerce 2.4.0: onbewerkte weergave van berichtgegevens op winkel](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md).
* [Bekende uitgave van Adobe Commerce 2.4.0: &quot;Selecties toevoegen aan mijn winkelwagentje&quot; werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md).
