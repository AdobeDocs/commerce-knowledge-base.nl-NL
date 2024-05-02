---
title: 'Bekende uitgave van ''Adobe Commerce 2.4.0: ontbrekend label ''Refund'' in Klarna'
description: Dit artikel biedt een oplossing voor een bekend probleem in Admin voor een ontbrekend **Refund**-label in Klarna VBE (Bundled Extension van leverancier). Wanneer in het portaal Klarna een restitutie wordt uitgevoerd, wordt het label **Resund** niet weergegeven naast het product uit de bundel dat is terugbetaald.
exl-id: f08039b2-7f8b-481e-8ec8-1659e227744f
feature: B2B, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# Bekende uitgave van Adobe Commerce 2.4.0: ontbrekend label &quot;Resund&quot; in Klarna

Dit artikel biedt een oplossing voor een bekende kwestie in Admin voor een ontbrekende **Terugbetaling** label in Klarna VBE (Vendor Bundled Extension). Wanneer in het portaal Klarna een restitutie wordt uitgevoerd, **Terugbetaling** label wordt niet weergegeven naast het product dat is gerestitueerd.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.0
* Adobe Commerce over cloudinfrastructuur 2.4.0

## Probleem

<u>Vereisten:</u>

* Klarna is ingeschakeld.
* Er wordt een gebundeld product gemaakt.

<u>Stappen om te reproduceren</u>

1. Ga naar Adobe Commerce en voeg een gebundeld product toe aan **karretje**.
1. Navigeer naar de kassa.
1. Consumenteninformatie invoeren bij afrekenen en klikken **Volgende**.
1. Selecteren **KP, optie** en klik op **Opdracht plaatsen**.
1. Ga naar **Beheerder** > **Verkoop** > **Orders**.
1. Open de volgorde.
1. Factuur maken voor product.
1. Ga naar **Facturen** > **Facturering selecteren** > Klik **Kredietfaciliteit** > Klik **Terugbetaling** (Niet **Offline terugbetalen**).
1. Ga naar Klarna portal.
1. Open de volgorde.
1. De **Terugbetaling** label aanwezig is.

<u>Verwacht resultaat</u>

Op het Klarna-portaal **Terugbetaling** wordt het label weergegeven naast het product dat is terugbetaald.

<u>Werkelijk resultaat</u>

Op het Klarna-portaal **Terugbetaling** label wordt niet weergegeven naast het product dat is terugbetaald.

## Workaround

De oplossing voor dit probleem is om de ontbrekende **Terugbetaling** in het Klarna-portaal voor terugbetaalde gebundelde producten. De restitutie heeft plaatsgevonden, ook al **Terugbetaling** label is niet weergegeven. Het probleem zal naar verwachting worden opgelost in Adobe Commerce 2.4.1, dat in het vierde kwartaal van 2020 zal worden gepubliceerd.

## Gerelateerde lezingen in onze kennisbasis voor ondersteuning:

* [Bekende uitgave van Adobe Commerce 2.4.0: onbewerkte weergave van berichtgegevens op winkel](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Export Tax Rates werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Betalingsmethoden voor Braintree worden niet weergegeven bij de afhandeling van meerdere adressen](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Foutbericht dat lokale betalingsmethode selecteert die in sommige landen wordt weergegeven tijdens het afrekenen](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: 404-fout bij het verwijderen van beloningspunten bij afhandeling via meerdere verzendingen](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: weergavefout voor bestellingen](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B Admin kan geen configureerbaar product toevoegen om te citeren](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Aanmaak van verzendlabels Bekend probleem in Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Bekende uitgave van Adobe Commerce 2.4.0 - Vernieuwen van de activiteiten van de Klant werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: &quot;Selecties toevoegen aan mijn winkelwagentje&quot; werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
