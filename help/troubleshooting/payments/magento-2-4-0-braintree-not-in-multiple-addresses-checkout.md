---
title: 'Adobe Commerce 2.4.0: Braintree niet in Multiple Address-uitchecken'
description: Dit artikel biedt een oplossing voor een bekende Adobe Commerce 2.4.0-probleem waarbij Braintree-betalingsmethoden niet zijn inbegrepen bij het werken met het afrekenen van meerdere adressen. De kwestie is opgelost in Adobe Commerce 2.4.1.
exl-id: efde0bba-fd4a-490b-becb-856cb9ea58a5
feature: Checkout, Compliance, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Braintree niet in Multiple Address-uitchecken

Dit artikel biedt een oplossing voor een bekende Adobe Commerce 2.4.0-probleem waarbij Braintree-betalingsmethoden niet zijn inbegrepen bij het werken met het afrekenen van meerdere adressen. De kwestie is opgelost in Adobe Commerce 2.4.1.

Nota: Adobe Commerce adviseert gebruikend de [&#x200B; uitbreiding van Braintree van Commerce Marketplace &#x200B;](https://marketplace.magento.com/paypal-module-braintree.html) voor versies 2.3 en later om de naleving van PSD te houden. De extensie biedt geen functionaliteit voor het afrekenen van meerdere adressen.

## Betrokken producten en versies

* Adobe Commerce op locatie v2.4.0
* Adobe Commerce op cloudinfrastructuur v2.4.0

## Probleem

<u> Eerste vereisten </u>:

De kernintegratie van Braintree wordt gebruikt.

<u> Stappen om </u> te reproduceren:

1. Ga naar de winkel.
1. Meld u aan als klant.
1. Voeg een product toe aan de kar.
1. Open je winkelwagentje.
1. De Mening van de pers **en geeft Kaart** uit.
1. De Controle van de pers **uit met Veelvoudige Adressen**.
1. De pers **gaat naar de Verzendinformatie**.
1. De pers **gaat aan het Factureren Informatie** voort.

<u> Verwacht resultaat </u>:

Braintree is beschikbaar als betalingsmethode.

<u> Werkelijk resultaat </u>:

Braintree is niet beschikbaar als betalingsmethode.

## Workaround

Schakel opties voor meerdere adressen niet in als u Braintree in Adobe Commerce 2.4.0 gebruikt. Dit probleem is opgelost in Adobe Commerce 2.4.1.

## Gerelateerde lezing in onze kennisbasis voor support

* [Bekende uitgave van Adobe Commerce 2.4.0 - Vernieuwen van de activiteiten van de Klant werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0 - Export Tax Rates werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: &quot;Selecties toevoegen aan mijn winkelwagentje&quot; werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
