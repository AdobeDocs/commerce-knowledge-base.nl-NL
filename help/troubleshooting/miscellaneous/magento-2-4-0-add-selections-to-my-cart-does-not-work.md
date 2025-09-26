---
title: 'Adobe Commerce 2.4.0: Selecties toevoegen aan mijn winkelwagentje werkt niet'
description: Dit artikel biedt een oplossing voor een probleem met een verbroken knop dat bekend is in de Commerce Admin wanneer u het winkelwagentje van een klant beheert. Wanneer u probeert geselecteerde producten toe te voegen aan het winkelwagentje van een klant, werkt de knop **Selecties toevoegen aan mijn winkelwagentje** aan de onderkant van de sectie niet. Dit probleem treedt op op op elke pagina in het beheerpaneel die twee **Selecties toevoegen aan de winkelwagentje** knoppen bevat. In Adobe Commerce 2.4.1 is een permanente oplossing beschikbaar.
exl-id: b0830ec2-2aea-4afb-8d02-e9c8f54283be
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Selecties toevoegen aan mijn winkelwagentje werkt niet

Dit artikel biedt een oplossing voor een probleem met een verbroken knop dat bekend is in de Commerce Admin wanneer u het winkelwagentje van een klant beheert. Wanneer het proberen om geselecteerde producten aan het winkelwagentje van een klant toe te voegen, **voegt selecties aan mijn wortel** knoop toe die op de bodem van de sectie wordt gevestigd niet. Deze kwestie komt op om het even welke Admin paneelpagina voor die twee **bevat toevoegt selecties aan mijn wortel** knopen. In Adobe Commerce 2.4.1 is een permanente oplossing beschikbaar.

## Betrokken producten en versies

* Adobe Commerce 2.4.0 (alle implementatiemethoden)

## Probleem

<u> Stappen om te reproduceren </u>

1. Navigeer aan om het even welke Admin paneelpagina die twee **bevat toevoegt selecties aan mijn wortel** knopen.
1. Selecteer objecten die je aan mijn winkelwagentje wilt toevoegen.
1. Klik **toevoegen selecties aan mijn wortel** knoop die op de bodem van de sectie wordt gevestigd.

<u> Verwacht resultaat </u>

Alle selecties worden aan mijn winkelwagentje toegevoegd zoals u had verwacht.

<u> Werkelijk resultaat </u>

Adobe Commerce voegt je selecties niet toe aan mijn winkelwagentje.

## Oplossing

**voegt selecties aan mijn wortel** knoop toe die op de bovenkant van de pagina wordt gevestigd nog werkt. Het probleem zal naar verwachting worden opgelost in Adobe Commerce versie 2.4.1, die in het vierde kwartaal van dit jaar zal worden uitgebracht.

## Gerelateerde lezing

* [ MerchDocs het Leiden een het Winkelen Kart ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage) in onze gebruikersgids.
* [ Adobe Commerce 2.4.0 gekende kwestie: De Tarieven van de Belasting van de uitvoer werken niet ](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md) in onze steunkennisbasis.
* [ Adobe Commerce 2.4.0 gekende kwestie: De betalingsmethodes van Braintree verschijnen niet in Veelvoudige Controle van Adressen ](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md) in onze basis van de steunkennis.
