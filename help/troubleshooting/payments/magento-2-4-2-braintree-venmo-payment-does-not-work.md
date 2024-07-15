---
title: "Adobe Commerce 2.4.2: Braintree betaling van Venmo werkt niet"
description: In dit artikel wordt een bekende Adobe Commerce 2.4.2-kwestie beschreven waarbij geen orders worden gegenereerd wanneer Braintree Venmo tijdens het afrekenen wordt gebruikt. Er is momenteel geen resolutie beschikbaar.
exl-id: 1832ab64-5024-444b-915e-473b34979a6e
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Adobe Commerce 2.4.2: Braintree betaling van Venmo werkt niet

In dit artikel wordt een bekende Adobe Commerce 2.4.2-kwestie beschreven waarbij geen orders worden gegenereerd wanneer Braintree Venmo tijdens het afrekenen wordt gebruikt. Er is momenteel geen resolutie beschikbaar.

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden) 2.4.2

## Probleem

<u> Voorwaarde </u>:

Betalingen via Venmo inschakelen in configuratie met Braintreeën.

<u> Stappen om </u> te reproduceren:

1. Voeg op de winkel artikelen toe aan het winkelwagentje.
1. Ga aan **Controle** te werk.
1. Selecteer de juiste verzendmethode.
1. Selecteer **Venmo** als betalingsmethode.
1. Klik **betalen met Venmo**.
1. Klik **orde van de Plaats**.

<u> Ware resultaten </u>:

De bestelling wordt niet in Adobe Commerce-code gemaakt nadat de klant vanuit de Venmo-app is omgeleid naar de winkel. Er wordt dan geen foutbericht weergegeven. De volgorde wordt in Braintree gemaakt.

<u> Verwachte resultaten </u>:

De bestelling wordt in Adobe Commerce gemaakt nadat de klant vanuit de Venmo-app naar de winkel is omgeleid en de bestelling in Braintree is gemaakt, zoals u had verwacht.

## Oplossing

Er is momenteel geen resolutie beschikbaar.
