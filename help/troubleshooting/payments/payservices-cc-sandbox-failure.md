---
title: Betalingen met creditcard zijn mislukt in een sandbox-omgeving
description: In dit artikel wordt uitgelegd waarom een testcreditcard mislukt in een Sandbox-omgeving met PayPal-API's.
exl-id: 65fd08e0-eefc-47f3-8964-bef3610e6182
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Betalingen met creditcard zijn mislukt in een sandbox-omgeving

In dit artikel wordt uitgelegd waarom een testcreditcard mislukt in een Sandbox-omgeving met PayPal-API&#39;s.

## Betrokken producten en versies


* Adobe Commerce 2.4.0 - 2.4.4, alle implementatieopties, met [Betalingsdiensten](https://marketplace.magento.com/magento-payment-services.html)

## Probleem

Bij gebruik van een Visa-creditcard `4111 1111 1111 1111` van PayPal mislukt het soms door het PayPal-fraudebeleid met de volgende fout:

```terminal
Error happened when processing the request. Please try again later.
```

## Oorzaak

Deze fout wordt weergegeven wanneer PayPal een specifiek creditcardnummer voor fraude weergeeft. Dit gebeurt omdat het een creditcardnummer is dat door iedereen overal ter wereld wordt gebruikt om met PayPal API&#39;s te testen.

## Oplossing

Gebruik een andere creditcard. Voor het genereren van modelcreditcards kunt u het testen:

1. Ga naar het PayPal Developer Portal [Creditcardmaatschappij](https://developer.paypal.com/developer/creditCardGenerator/) pagina.
1. Meld u aan bij het PayPal Developer Portal-dashboard.
1. Genereer een testcreditcard.
