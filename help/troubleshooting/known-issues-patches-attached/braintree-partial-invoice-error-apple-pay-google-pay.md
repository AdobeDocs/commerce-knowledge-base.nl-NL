---
title: 'Adobe Commerce 2.4.4: Onbekwaam om gedeeltelijke facturen te creëren'
description: Dit artikel bevat een hotfix voor het probleem waarbij gebruikers geen gedeeltelijke facturen kunnen maken wanneer ze Apple Pay of Google Pay via Braintree als betalingsmethode gebruiken.
exl-id: bf78cc07-9dc7-4eb8-bfdf-57ea5131effb
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Adobe Commerce 2.4.4: Onbekwaam om gedeeltelijke facturen te creëren

Dit artikel bevat een hotfix voor het probleem waarbij gebruikers geen gedeeltelijke facturen kunnen maken wanneer ze Apple Pay of Google Pay via Braintree als betalingsmethode gebruiken.

## Betrokken producten en versies

Adobe Commerce (alle implementatiemethoden) 2.4.4

## Probleem

Wanneer het gebruiken van Betalen Apple of Google als betalingsmethodes, krijgen de gebruikers de fout &quot;*het bevel &quot;vault_capture&quot;niet bestaat. Controleer de opdracht en probeer het opnieuw.* &quot; tijdens het maken van gedeeltelijke facturen.

<u> Stappen om </u> te reproduceren:

1. Open uw Adobe Commerce-website.
1. Voeg een eenvoudig product toe aan de wagen (hoeveelheid 2).
1. Kies **Apple Betalen** of **Google Betalen** als betalingsmethode van het het winkelwagentje.
1. Plaats de bestelling.
1. Open bestelgegevens vanaf de achterkant.
1. Maak een gedeeltelijke factuur.
1. Maak een andere factuur voor het resterende bedrag.

<u> Verwachte resultaten </u>:

Gedeeltelijke facturen worden gemaakt.

<u> Ware resultaten </u>:

De eerste gedeeltelijke factuur wordt gemaakt. Tijdens het creëren van de tweede gedeeltelijke factuur, krijgen de gebruikers de volgende fout: *het bevel &quot;vault_capture&quot;bestaat niet. Verifieer het bevel en probeer opnieuw*.

## Oorzaak

Adobe Commerce slaat creditcardgegevens op in de vault om gedeeltelijke facturen te maken. Er is momenteel geen functionaliteit om Apple Pay en Google Pay in te schakelen.

## Oplossing

Pas de volgende patch toe om het probleem op te lossen:

[Braintree_disabled_part_capture_for_applepay_googlepay.zip](assets/braintree-disabled-partial-capture-for-applepay-googlepay.zip)

## Hoe de pleister moet worden aangebracht

Zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies wordt verstrekt.
