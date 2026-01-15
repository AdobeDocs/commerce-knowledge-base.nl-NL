---
title: Adobe Commerce 2.4.0-installatie mislukt met verouderde opslagcache
description: 'Dit artikel biedt een oplossing voor het probleem waarbij de Adobe Commerce 2.4.0-installatie mislukt met het foutbericht: *De standaardwebsite is niet gedefinieerd. Stel de website in en probeer het opnieuw.* weergegeven in de console.'
exl-id: 0680199b-7e47-4a8c-91fe-9f6c32839a0e
feature: B2B, Cache, Console, Install, Upgrade
role: Developer
source-git-commit: 05297c82b292b8ccc88018c58e991bd3a32d6ffa
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Adobe Commerce 2.4.0-installatie mislukt met verouderde opslagcache

Dit artikel verstrekt een oplossing voor de kwestie waar uw installatie van Adobe Commerce 2.4.0 met het foutenmelding ontbreekt: *de standaardwebsite wordt niet bepaald. Stel de website in en probeer het opnieuw.* weergegeven in de console.

## Betrokken producten en versies

* Adobe Commerce over cloudinfrastructuur 2.4.0
* Adobe Commerce op locatie 2.4.0

## Probleem

<u> Eerste vereisten:</u>
Een derdeuitbreiding met gebiedsdelen op APIs voor de module van de Opslag in CLI bevelen wordt gevormd zoals vereist in `composer.json`. Dit veroorzaakt de installatie van Adobe Commerce 2.4.0 om met een foutenmelding te ontbreken: *de standaardwebsite wordt niet bepaald. Stel de website in en probeer het opnieuw.* weergegeven in de console.

## Oorzaak

De kwestie verschijnt voor de derdeuitbreidingen die van opslag in hun CLI bevelen afhankelijk zijn. Eén is Amazon Sales Channel.

## Oplossing

Voor de installatie van Adobe Commerce 2.4.0 moeten handelaren:

1. Verwijder deze extensies van derden uit `composer.json` .
1. Installeer Adobe Commerce zonder extensies.
1. Voeg de extensies toe na de installatie.

De kwestie zal in het toepassingsgebied van 2.4.1 versie worden bepaald.

## Gerelateerde lezingen in onze kennisbasis voor ondersteuning:

* [Bekende uitgave van Adobe Commerce 2.4.0: ontbrekend label &quot;Resund&quot; in Klarna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Adobe Commerce 2.4.0, 2.4.1: Enable Braintree Venmo Part Celling Issue](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Foutbericht dat lokale betalingsmethode selecteert die in sommige landen wordt weergegeven tijdens het afrekenen](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Amazon Pay ingeschakeld, betalingsmethoden ontbreken wanneer Terug naar standaardafhandeling wordt gebruikt](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Adobe Commerce 2.4.0 B2B Admin kan geen configureerbaar product toevoegen om te citeren](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Betalingsmethoden van Braintree worden niet weergegeven bij de afhandeling van meerdere adressen](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)

