---
title: 'Adobe Commerce 2.4.0: Selecties toevoegen aan mijn winkelwagentje werkt niet'
description: Dit artikel biedt een oplossing voor een probleem met een verbroken knop dat bekend is in de Commerce Admin wanneer u het winkelwagentje van een klant beheert. Wanneer u probeert geselecteerde producten toe te voegen aan het winkelwagentje van een klant, werkt de knop **Selecties toevoegen aan mijn winkelwagentje** aan de onderkant van de sectie niet. Dit probleem treedt op op op elke pagina in het beheerpaneel die twee **Selecties toevoegen aan de winkelwagentje** knoppen bevat. In Adobe Commerce 2.4.1 is een permanente oplossing beschikbaar.
exl-id: b0830ec2-2aea-4afb-8d02-e9c8f54283be
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Selecties toevoegen aan mijn winkelwagentje werkt niet

Dit artikel biedt een oplossing voor een probleem met een verbroken knop dat bekend is in de Commerce Admin wanneer u het winkelwagentje van een klant beheert. Wanneer u bepaalde producten aan het winkelwagentje van een klant probeert toe te voegen, **Selecties toevoegen aan mijn winkelwagentje** de knop onder aan de sectie werkt niet. Dit probleem doet zich voor op elke pagina in het deelvenster Beheer die twee **Selecties toevoegen aan mijn winkelwagentje** knoppen. In Adobe Commerce 2.4.1 is een permanente oplossing beschikbaar.

## Betrokken producten en versies

* Adobe Commerce 2.4.0 (alle implementatiemethoden)

## Probleem

<u>Stappen om te reproduceren</u>

1. Navigeer naar een pagina in het deelvenster Beheer die twee pagina&#39;s bevat **Selecties toevoegen aan mijn winkelwagentje** knoppen.
1. Selecteer objecten die je aan mijn winkelwagentje wilt toevoegen.
1. Klik op de knop **Selecties toevoegen aan mijn winkelwagentje** onder aan de sectie.

<u>Verwacht resultaat</u>

Alle selecties worden aan mijn winkelwagentje toegevoegd zoals u had verwacht.

<u>Werkelijk resultaat</u>

Adobe Commerce voegt je selecties niet toe aan mijn winkelwagentje.

## Oplossing

De **Selecties toevoegen aan mijn winkelwagentje** de knop boven aan de pagina werkt nog steeds. Het probleem zal naar verwachting worden opgelost in Adobe Commerce versie 2.4.1, die in het vierde kwartaal van dit jaar zal worden uitgebracht.

## Gerelateerde lezing

* [MerchDocs&#39; Een winkelwagentje beheren](https://docs.magento.com/user-guide/sales/shopping-assisted-cart-manage.html) in onze gebruikershandleiding.
* [Bekende uitgave van Adobe Commerce 2.4.0: onbewerkte weergave van berichtgegevens op winkel](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md) in onze kennisbasis voor ondersteuning.
* [Bekende uitgave van Adobe Commerce 2.4.0: Export Tax Rates werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md) in onze kennisbasis voor ondersteuning.
* [Bekende uitgave van Adobe Commerce 2.4.0: Betalingsmethoden voor Braintree worden niet weergegeven bij de afhandeling van meerdere adressen](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md) in onze kennisbasis voor ondersteuning.
