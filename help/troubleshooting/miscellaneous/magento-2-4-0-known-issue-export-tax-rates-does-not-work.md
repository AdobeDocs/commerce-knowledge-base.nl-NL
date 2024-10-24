---
title: Bekende uitgave van Adobe Commerce 2.4.0 - Export Tax Rates werkt niet
description: Dit artikel biedt een oplossing voor een bekende Adobe Commerce 2.4.0-probleem waarbij de knop **Exportbelastingen** niet werkt.
exl-id: 29a34a1f-d23a-43cb-ac1f-8711ce25fa6c
feature: Data Import/Export, Orders
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Bekende uitgave van Adobe Commerce 2.4.0 - Export Tax Rates werkt niet

Dit artikel verstrekt een oplossing voor een bekende kwestie van Adobe Commerce 2.4.0 waar de **knoop van de Tarieven van de Uitvoer** niet werkt.

## Betrokken producten en versies

* Adobe Commerce over cloudinfrastructuur 2.4.0
* Adobe Commerce op locatie 2.4.0

## Probleem

<u> Stappen om te reproduceren:</u>

1. Ga naar het Comité van Admin van Commerce > **Opslag** > **de Regels van de Belasting**.
1. Klik **toevoegen Nieuwe knoop van de Regel van de Belasting**.
1. Klik op de tekst van de **knoop van de Tarieven van de Uitvoer**.

   ![ magento_export_tax_rates.png ](assets/mceclip0.png)

<u> Verwacht resultaat </u>:

Een `tax_rates.csv` -bestand dat belastingtarieven bevat.

<u> Werkelijk resultaat </u>:

Er wordt geen CSV-bestand gedownload.

## Oplossing

Oplossing:

Klik op de bodem linkerrand van de **knoop van de Tarieven van de Uitvoer van de Belasting** om het `tax_rates.csv` dossier uit te voeren.

![ magento_export_tax_rates.png ](assets/mceclip1.png)

Het probleem wordt opgelost in een 2.4.1-patch.

## Gerelateerde lezing

In onze kennisbasis voor ondersteuning:

* [ Adobe Commerce 2.4.0 gekende kwestie: De betalingsmethodes van de Braintree verschijnen niet in Veelvoudige Controle van Adressen ](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md).
* [ Adobe Commerce 2.4.0 gekende kwestie - verfrist zich op de Activiteiten van de Klant werkt niet ](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md).
* [ Adobe Commerce 2.4.0 gekende kwestie: de ruwe vertoning van berichtgegevens op storefront ](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md).
* [ Adobe Commerce 2.4.0 bekende kwestie: &quot;voeg selecties aan mijn wortel&quot;knoop toe werkt niet ](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md).
