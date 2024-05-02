---
title: "Adobe Commerce 2.4.2 B2B: disconto blijft wijziging loonmethode"
description: In dit artikel wordt een bekende Adobe Commerce 2.4.2 B2B-uitgifte beschreven waarbij een aan een betalingsmethode gekoppelde korting blijft bestaan nadat een betalingsmethode bij de kassa is gewijzigd. Er is momenteel geen resolutie beschikbaar.
exl-id: cd863852-403b-404f-8717-c78c238f5f33
feature: B2B, Orders, Payments, Personalization
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Adobe Commerce 2.4.2 B2B: disconto blijft wijziging loonmethode

In dit artikel wordt een bekende Adobe Commerce 2.4.2 B2B-uitgifte beschreven waarbij een aan een betalingsmethode gekoppelde korting blijft bestaan nadat een betalingsmethode bij de kassa is gewijzigd. Er is momenteel geen resolutie beschikbaar.

## Betrokken producten en versies

* Adobe Commerce 2.4.2
* Adobe Commerce over wolkeninfrastructuur 2.4.2
* B2B voor Adobe Commerce 1.3.1


## Probleem

<u>Stappen om te reproduceren</u> :

1. Een winkelwagentje maken **Prijsregel** die aan een betalingsmethode is gekoppeld (Voorbeeld: PayPal-gebruikers krijgen een korting van 20%.)
1. Maak een inkooporder (inkooporder) en selecteer PayPal als betalingsmethode. De korting wordt toegepast.
1. De PO is goedgekeurd.
1. Ga naar de betalingspagina om de bestelling te voltooien.
1. Selecteer een andere betalingsmethode.

<u>Werkelijke resultaten</u> :

De korting op de betalingsmethode blijft van toepassing op het totaal van de bestelling.  Er wordt geen foutbericht weergegeven. De eigenaar van de winkel kan dit zien door de ordergeschiedenis te controleren.

<u>Verwachte resultaten</u> :De korting op de betalingsmethode wordt verwijderd uit het totaal van de bestelling, zoals u had verwacht.

## Oplossing

Er is momenteel geen resolutie beschikbaar.
