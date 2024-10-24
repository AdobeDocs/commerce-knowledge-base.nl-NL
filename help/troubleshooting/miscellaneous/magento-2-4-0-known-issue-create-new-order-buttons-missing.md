---
title: 'Bekende uitgave voor Adobe Commerce 2.4.0: knoppen voor nieuwe volgorde ontbreken'
description: Dit artikel biedt een oplossing voor een bekend probleem in Commerce Admin voor twee ontbrekende knoppen op de pagina voor het maken van bestellingen. Wanneer u een nieuwe bestelling maakt voor een nieuwe of bestaande klant, is het niet mogelijk om producten aan de bestelling uit de catalogus toe te voegen omdat de knoppen **Producten toevoegen door SKU** en **Producten toevoegen*** ontbreken. Dit wordt veroorzaakt doordat JS-bundeling wordt ingeschakeld. Een oplossing is beschikbaar in Adobe Commerce 2.4.1.
exl-id: 24ae880e-6d74-4444-9165-2744b12af81a
feature: B2B
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Bekende uitgave van Adobe Commerce 2.4.0: knoppen Nieuwe volgorde maken ontbreken

Dit artikel biedt een oplossing voor een bekend probleem in Commerce Admin voor twee ontbrekende knoppen op de pagina voor het maken van bestellingen. Wanneer het creëren van een nieuwe orde voor een nieuwe of bestaande klant, is het niet mogelijk om producten aan de orde van de catalogus toe te voegen aangezien **Producten door SKU** toevoegt en **toevoegt de knopen van Producten** ontbreken. Dit wordt veroorzaakt doordat JS-bundeling wordt ingeschakeld. Een oplossing is beschikbaar in Adobe Commerce 2.4.1.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.0
* Adobe Commerce over cloudinfrastructuur 2.4.0

## Probleem

<u> Stappen om te reproduceren </u>

1. Ga naar **Klanten > Alle Klanten**.
1. Klik **uitgeven** verbinding op een klant.
1. Klik de **Create Orde** knoop.

<u> Verwacht resultaat </u>

**voegt Producten door SKU** toe en **voegt Producten** knopen op **verschijnen tot Nieuwe orde** pagina toe.

<u> Werkelijk resultaat </u>

**voegt Producten door SKU** toe en **voegt Producten** knopen toe ontbreken op **creeer Nieuwe orde** pagina.

## Workaround

De oplossing voor deze kwestie is het maken van JS-pakketten voor de Adobe Commerce-instantie uit te schakelen. Het probleem zal naar verwachting worden opgelost in Adobe Commerce 2.4.1, dat in het vierde kwartaal van 2020 zal worden gepubliceerd.

## Gerelateerde lezingen in onze kennisbasis voor ondersteuning

* [Bekende uitgave van Adobe Commerce 2.4.0: onbewerkte weergave van berichtgegevens op winkel](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Export Tax Rates werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Betalingsmethoden voor Braintree worden niet weergegeven bij de afhandeling van meerdere adressen](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Foutbericht dat lokale betalingsmethode selecteert die in sommige landen wordt weergegeven tijdens het afrekenen](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: 404-fout bij het verwijderen van beloningspunten bij afhandeling via meerdere verzendingen](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: weergavefout voor bestellingen](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B Admin kan geen configureerbaar product toevoegen om te citeren](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Bekende uitgave van Adobe Commerce 2.4.0 - Vernieuwen van de activiteiten van de Klant werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: &quot;Selecties toevoegen aan mijn winkelwagentje&quot; werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
