---
title: "Adobe Commerce 2.4.0, 2.4.1: Enable Braintree Venmo Part Bill"
description: In dit artikel wordt een bekende uitgave van Adobe Commerce 2.4.0 en 2.4.1 beschreven, waarbij een gedeeltelijke factuur niet beschikbaar is voor bestellingen die via Braintree via Venmo worden geplaatst.
exl-id: ef6c8aa4-a2a7-4e07-a957-23173017baf2
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Adobe Commerce 2.4.0, 2.4.1: Braintree Venmo gedeeltelijke factuur toestaan

In dit artikel wordt een bekende uitgave van Adobe Commerce 2.4.0 en 2.4.1 beschreven, waarbij een gedeeltelijke factuur niet beschikbaar is voor bestellingen die via Braintree via Venmo worden geplaatst.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.0 en 2.4.1
* Adobe Commerce over wolkeninfrastructuur 2.4.0 en 2.4.1

## Probleem

<u> Eerste vereisten:</u>

In de configuratie van de betalingsmethode van de Braintree, plaats **laat Venmo door Braintree** toe = *ja* met **de Actie van de Betaling** = *Vergunning*; **laat vault voor de Betalingen van de Kaart** toe = *Nr*.

<u> Stappen om te reproduceren:</u>

1. Maak een bestelling voor twee of meer producten, waarbij Venmo (Braintree) wordt gebruikt als betalingsmethode.
1. Open de volgorde in Commerce Admin.
1. Maak een factuur voor een van de bestelde producten.
1. Probeer facturen te maken voor de overige bestelde producten.

<u> Verwacht resultaat:</u>

Factuur gemaakt.

<u> Ware resultaat:</u>

Het volgende foutbericht wordt weergegeven: *De opdracht &quot;vault\_capture&quot; bestaat niet. Verifieer het bevel en probeer opnieuw.*

## Workaround

Vang het volledige bedrag op bij het maken van facturen voor bestellingen die met behulp van Braintree via Venmo zijn geplaatst.
