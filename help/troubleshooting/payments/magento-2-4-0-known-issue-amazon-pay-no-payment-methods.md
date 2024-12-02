---
title: 'Bekende uitgave van Adobe Commerce 2.4.0: Amazon-betaling, geen betalingsmethoden'
description: Dit artikel biedt een oplossing voor een bekende Adobe Commerce 2.4.0-probleem waarbij betalingsmethoden ontbreken wanneer klanten **Terug naar standaardafhandeling*** gebruiken nadat ze Amazon hebben ingeschakeld.
exl-id: efd792c7-8970-4366-b9d1-4bf284ea96db
feature: B2B, Orders, Payments
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Bekende uitgave van Adobe Commerce 2.4.0: Amazon-betaling, geen betalingsmethoden

Dit artikel verstrekt een oplossing voor een bekende kwestie van Adobe Commerce 2.4.0 waar de betalingsmethodes ontbreken wanneer de klanten **Terugkeer aan standaardcontrole** gebruiken, nadat zij Amazon toelagen.

## Betrokken producten en versies

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur v2.3.5.p1 en v2.4.0

<u> Stappen om te reproduceren:</u>

1. Ga naar de storefront.
1. Voeg een willekeurig item aan het winkelwagentje toe en ga verder met het afrekenen.
1. Meld u aan bij uw Amazon Pay-account.
1. Selecteer een adres en ga door naar de kassa.
1. Klik **Terugkeer aan standaardcontrole**.
1. Ga door naar de kassa.

<u> Verwachte resultaten:</u>

Betalingsmethoden moeten worden weergegeven nadat het afrekenen opnieuw is gestart.

<u> Ware resultaten:</u>

Betalingsmethoden ontbreken.

## Oplossing

Voor 2.4.1 is een resolutie gepland.

## Gerelateerde lezingen in onze kennisbasis voor ondersteuning:

* [Bekende uitgave van Adobe Commerce 2.4.0: Foutbericht dat lokale betalingsmethode selecteert die in sommige landen wordt weergegeven tijdens het afrekenen](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: 404-fout bij het verwijderen van beloningspunten bij afhandeling via meerdere verzendingen](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: weergavefout voor bestellingen](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B Admin kan geen configureerbaar product toevoegen om te citeren](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Betalingsmethoden voor Braintree worden niet weergegeven bij de afhandeling van meerdere adressen](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekende uitgave van Adobe Commerce 2.4.0 - Vernieuwen van de activiteiten van de Klant werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0 - Export Tax Rates werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: &quot;Selecties toevoegen aan mijn winkelwagentje&quot; werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: onbewerkte weergave van berichtgegevens op winkel](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
