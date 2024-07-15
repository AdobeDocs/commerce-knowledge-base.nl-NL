---
title: 'Adobe Commerce 2.4.0: Afhandelingsfout bij het selecteren van lokale betalingen'
description: '''In dit artikel wordt gesproken over een oplossing voor een bekend probleem in Adobe Commerce tijdens het afrekenen, waarbij een foutbericht wordt weergegeven wanneer een lokale betalingsmethode wordt geselecteerd voor sommige landen. Dit geldt voor de landen België, Italië, Nederland, Polen en Spanje."'
exl-id: de2eafb0-d03c-4ff8-9615-0f2676d95848
feature: B2B, Categories, Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Afhandelingsfout bij het selecteren van lokale betalingen

In dit artikel wordt gesproken over een oplossing voor een bekend probleem in Adobe Commerce tijdens het afrekenen, waarbij een foutbericht wordt weergegeven wanneer een lokale betalingsmethode wordt geselecteerd voor sommige landen. Dit geldt voor de landen België, Italië, Nederland, Polen en Spanje.

Het foutenbericht, &quot;*Er zijn momenteel geen beschikbare betalingsmethodes. Werk uw factureringsadres bij.* wordt weergegeven, maar de lokale betalingsmethoden worden wel weergegeven en werken correct. In Adobe Commerce 2.4.1 is een permanente oplossing beschikbaar.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.0
* Adobe Commerce over cloudinfrastructuur 2.4.0

## Probleem

<u> Eerste vereisten </u>:

* Adobe Commerce 2.4.0 is geïnstalleerd.
* Maak één product en één categorie.
* Vorm [ de Methode van de Betaling van de Braintree ](https://devdocs.magento.com/guides/v2.4/graphql/payment-methods/braintree.html).

<u> Stappen om </u> te reproduceren:

1. Ga naar de storefront.
1. Selecteer de items die u aan het winkelwagentje wilt toevoegen.
1. Ga door met de kassa.
1. Vul het adresformulier in met een geldig adres.
1. Ga naar de pagina Controleren en betalen.

<u> Verwacht resultaat </u>:

De lokale betalingsmethoden moeten normaal worden weergegeven, zonder een foutbericht.

<u> Werkelijk resultaat </u>:

Het foutenbericht, &quot;*Er zijn momenteel geen beschikbare betalingsmethodes. Werk uw factureringsadres bij.* &quot; weergegeven, maar de lokale betalingsmethoden worden wel correct weergegeven en functioneren.

## Oplossing

De oplossing is het weergegeven foutbericht te negeren en de betaling als normaal te laten verlopen, aangezien alle lokale betalingsmethoden normaal zullen werken. De oplossing was beschikbaar vanaf Adobe Commerce versie 2.4.1.

## Gerelateerde lezing

* [Bekende uitgave van Adobe Commerce 2.4.0: onbewerkte weergave van berichtgegevens op winkel](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Export Tax Rates werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Betalingsmethoden voor Braintree worden niet weergegeven bij de afhandeling van meerdere adressen](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: retourneert bewerkingspagina werkt niet meer bij het maken van een verzendlabel](/help/troubleshooting/known-issues-patches-attached/magento-2-4-0-patch-returns-shipping-label-creation-issue.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Vernieuwen van activiteiten van de Klant werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B Admin kan geen configureerbaar product toevoegen om te citeren](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
