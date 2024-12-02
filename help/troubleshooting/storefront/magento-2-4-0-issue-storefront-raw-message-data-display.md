---
title: 'Uitgave Adobe Commerce 2.4.0: weergave van onbewerkte berichtgegevens in winkel'
description: Dit artikel biedt een oplossing voor het probleem wanneer alle foutberichten op de storefront worden weergegeven met een plusteken (+) in plaats van een spatie. Deze oplossing helpt foutmeldingen leesbaar te blijven.
exl-id: f44fe434-a320-4e7e-a876-9575921749f3
feature: Storefront
role: Admin
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# Uitgave Adobe Commerce 2.4.0: weergave van onbewerkte berichtgegevens in winkel

Dit artikel biedt een oplossing voor het probleem wanneer alle foutberichten op de storefront worden weergegeven met een plusteken (+) in plaats van een spatie. Deze oplossing helpt foutmeldingen leesbaar te blijven.

## Betrokken producten en versies

* Adobe Commerce over cloudinfrastructuur 2.4.0
* Adobe Commerce op locatie 2.4.0.

## Probleem

<u> Stappen om te reproduceren:</u>

1. Ga naar **Create Nieuwe pagina van de Rekening** op de storefront.
1. Maak een nieuw account met een geregistreerd e-mailadres. Het volgende bericht wordt weergegeven:

`There+is+already+an+account+with+this+email+address.+If+you+are+sure+that+it+is+your+email+address,+click+here+to+get+your+password+and+access+your+account.`

## Oorzaak

Het probleem wordt veroorzaakt door een PHP 7.4.2 uitgave met betrekking tot set\\read cookies. Zie [ PHP BUG \#79174 setcookie() codeert ruimte als \`+\`, maar $\_COOKIE decodeert hen niet meer ](https://bugs.php.net/bug.php?id=79174).

## Oplossing

Gebruik een andere versie van PHP 7.4.x om dit probleem op te lossen. PHP 7.4.2 wordt niet ondersteund door Adobe Commerce 2.4.0.

## Gerelateerde lezingen in onze kennisbasis voor ondersteuning:

* [Bekende uitgave van Commerce 2.4.0: Betalingsmethoden voor Braintree worden niet weergegeven bij de afhandeling van meerdere adressen](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Vernieuwen op activiteiten van de klant werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Export Tax Rates werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: &quot;Selecties toevoegen aan mijn winkelwagentje&quot; werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
