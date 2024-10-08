---
title: Betalingen met creditcard zijn mislukt in een sandbox-omgeving
description: In dit artikel wordt uitgelegd waarom een testcreditcard mislukt in een Sandbox-omgeving met PayPal-API's.
exl-id: 65fd08e0-eefc-47f3-8964-bef3610e6182
feature: Orders, Payments
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Betalingen met creditcard zijn mislukt in een sandbox-omgeving

In dit artikel wordt uitgelegd waarom een testcreditcard mislukt in een Sandbox-omgeving met PayPal-API&#39;s.

## Betrokken producten en versies


* Adobe Commerce 2.4.0 - 2.4.4, alle plaatsingsopties, met [ de Diensten van de Betaling ](https://marketplace.magento.com/magento-payment-services.html)

## Probleem

Wanneer u een Visa-creditcard test van PayPal gebruikt, mislukt deze soms door PayPal-fraudebeleid met de volgende fout:`4111 1111 1111 1111`

```bash
Error happened when processing the request. Please try again later.
```

## Oorzaak

Deze fout wordt weergegeven wanneer PayPal een specifiek creditcardnummer voor fraude weergeeft. Dit gebeurt omdat het een creditcardnummer is dat door iedereen overal ter wereld wordt gebruikt om met PayPal API&#39;s te testen.

## Oplossing

Gebruik een andere creditcard. Voor het genereren van modelcreditcards kunt u het testen:

1. Ga naar de pagina van de Generator van de Kredietkaart van het Portaal van de Ontwikkelaar van PayPal [.](https://developer.paypal.com/developer/creditCardGenerator/)
1. Meld u aan bij het PayPal Developer Portal-dashboard.
1. Genereer een testcreditcard.
