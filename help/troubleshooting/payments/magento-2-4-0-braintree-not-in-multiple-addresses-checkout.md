---
title: 'Adobe Commerce 2.4.0: Braintree niet bij het uitchecken van meerdere adressen'
description: Dit artikel biedt een oplossing voor een bekende Adobe Commerce 2.4.0-probleem waarbij betalingsmethoden voor Braintreeën niet zijn inbegrepen bij het werken met de afhandeling Meerdere adressen. De kwestie is opgelost in Adobe Commerce 2.4.1.
exl-id: efde0bba-fd4a-490b-becb-856cb9ea58a5
feature: Checkout, Compliance, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Braintree niet in Multiple Addressen uitchecken

Dit artikel biedt een oplossing voor een bekende Adobe Commerce 2.4.0-probleem waarbij betalingsmethoden voor Braintreeën niet zijn inbegrepen bij het werken met de afhandeling Meerdere adressen. De kwestie is opgelost in Adobe Commerce 2.4.1.

Opmerking: Adobe Commerce raadt u aan de [Commerce Marketplace Braintree extensie](https://marketplace.magento.com/paypal-module-braintree.html) voor versies 2.3 en hoger om de PSD-compatibiliteit te behouden. De extensie biedt geen functionaliteit voor het afrekenen van meerdere adressen.

## Betrokken producten en versies

* Adobe Commerce op locatie v2.4.0
* Adobe Commerce op cloudinfrastructuur v2.4.0

## Probleem

<u>Vereisten</u>:

De belangrijkste integratie van de Braintree wordt gebruikt.

<u>Stappen om te reproduceren</u>:

1. Ga naar de winkel.
1. Meld u aan als klant.
1. Voeg een product toe aan de kar.
1. Open je winkelwagentje.
1. Druk **Winkelwagentje weergeven en bewerken**.
1. Druk **Uitchecken met meerdere adressen**.
1. Druk **Ga naar Verzendgegevens**.
1. Druk **Doorgaan met factureringsgegevens**.

<u>Verwacht resultaat</u>:

Braintree is beschikbaar als betalingsmethode.

<u>Werkelijk resultaat</u>:

Braintree is niet beschikbaar als betalingsmethode.

## Workaround

Schakel opties voor meerdere adressen niet in als u Braintree gebruikt in Adobe Commerce 2.4.0. Dit probleem is opgelost in Adobe Commerce 2.4.1.

## Gerelateerde lezing in onze kennisbasis voor support

* [Bekende uitgave van Adobe Commerce 2.4.0 - Vernieuwen van de activiteiten van de Klant werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Aanmaak van verzendlabels Bekend probleem in Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: onbewerkte weergave van berichtgegevens op winkel](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekende uitgave van Adobe Commerce 2.4.0 - Export Tax Rates werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: &quot;Selecties toevoegen aan mijn winkelwagentje&quot; werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
