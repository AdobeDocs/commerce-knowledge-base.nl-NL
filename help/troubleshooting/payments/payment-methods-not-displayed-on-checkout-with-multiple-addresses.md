---
title: Betalingsmethoden worden niet weergegeven bij afrekenen met meerdere adressen
description: In dit artikel wordt uitgelegd dat de meeste betalingsmethoden niet worden weergegeven bij het afrekenen wanneer meerdere verzendadressen zijn opgegeven, omdat de functionaliteit alleen voor Cybersource is geïmplementeerd.
exl-id: 68a9ee77-d0ef-43c5-9667-6d099b797666
feature: Checkout, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Betalingsmethoden worden niet weergegeven bij afrekenen met meerdere adressen

In dit artikel wordt uitgelegd dat de meeste betalingsmethoden niet worden weergegeven bij het afrekenen wanneer meerdere verzendadressen zijn opgegeven, omdat de functionaliteit alleen voor Cybersource is geïmplementeerd.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.x.x
* Adobe Commerce op cloudinfrastructuur 2.x.x

>[!NOTE]
>
>De belangrijkste integratie van Adobe Commerce Cybersource-betalingen is sinds 2.3.3 verouderd en zal in 2.4.0 volledig worden verwijderd. Gebruik in plaats hiervan de [ officiële uitbreiding ](https://marketplace.magento.com/cybersource-global-payment-management.html) van Marketplace.

## Probleem

<u> Vereisten </u>: In Commerce Admin, laat en vormt PayPal en Cybersource betalingsmethodes toe, en laat MultiShipping voor uw opslag toe.

<u> Stappen om </u> te reproduceren:

1. Voeg in de winkel meerdere producten toe aan de winkelwagentje.
1. Ga naar de winkelwagentje pagina.
1. Klik **Controle uit met Veelvoudige Adressen**.
1. Meld u aan of maak account.
1. Splits omhoog producten tussen de adressen op de Schip aan Veelvoudige pagina van Adressen.
1. Klik **gaan naar de Verzendinformatie**.
1. Selecteer verzendmethoden voor elke verzending.
1. Klik **blijven aan het Factureren Informatie**.

<u> Verwacht resultaat </u>: PayPal en Cybersource zijn beschikbaar als betalingsopties.

<u> Ware resultaat </u>: Slechts verschijnt Cybersource als beschikbare betalingsoptie.

## Oorzaak

Cybersource is momenteel de enige ondersteunde live betalingsmethode voor het afrekenen van meerdere verzendingen, vanaf versie 2.2.4. Ondersteuning voor multiShipping wordt voor elke betalingsmethode waarschijnlijk één voor één samengesteld. Er kunnen momenteel geen exacte datums of releasenummers worden opgegeven.
