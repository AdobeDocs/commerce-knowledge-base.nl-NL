---
title: "Adobe Commerce 2.4.0: Vernieuwen van de activiteiten van de Klant werkt niet"
description: Dit artikel biedt een oplossing voor een bekend probleem met Adobe Commerce 2.4.0 wanneer een beheerder een bestelling voor een klant maakt en de vernieuwingsknoppen in het zijpaneel Activiteiten van de klant niet werken.
exl-id: 50048e9f-6009-4db5-ae4a-c35a84cec265
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: Vernieuwen van de activiteiten van de Klant werkt niet

Dit artikel biedt een oplossing voor een bekend probleem met Adobe Commerce 2.4.0 wanneer een beheerder een bestelling voor een klant maakt en de vernieuwingsknoppen in het zijpaneel Activiteiten van de klant niet werken.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.0
* Adobe Commerce over cloudinfrastructuur 2.4.0

## Probleem

<u> Stappen om </u> te reproduceren:

1. Ga naar het **Comité Admin** > **Verkoop** > **Orders**.
1. Klik **creëren Nieuwe Orde** knoop.
1. Selecteer de klant die u hebt gemaakt.
1. Ga naar de winkel als de nieuwe klant.
1. Ga naar de **pagina van het Product**. Klik **verfrissen** knoop op de **onlangs Bekeken Producten** sectie van **Activiteiten van de Klant**.
1. Ga terug naar de winkel.
1. Plaats een bestelling met de gemaakte producten.
1. Ga terug naar het **Comité Admin** en klik **verfrissen** knoop van de **Laatste Bestelde Punten** sectie van **Activiteiten van de Klant**.
1. Ga terug naar de winkel. Voeg het gecreeerde product aan de **Vergelijkingslijst** toe.
1. Ga terug naar het **Comité Admin**. Klik **verfrissen** knoop van de **Producten in de sectie van de Lijst van de Vergelijking** van **Activiteiten van de Klant**.
1. Ga terug naar de winkel.
1. Verwijder het gecreeerde product uit de **Lijst van de Vergelijking**.
1. Ga terug naar het **Comité Admin**.
1. Klik **verfrissen** knoop van de **onlangs Vergelijkte Producten** sectie van **Activiteiten van de Klant**.
1. Ga terug naar de winkel.

<u> Verwachte resultaten </u>:

De naam van het product zou in de **onlangs Bekeken Producten**, **Laatste Bestelde Punten**, **Producten in Vergelijkingslijst**, en **onlangs Vergeleken de sectie van Producten** moeten verschijnen.

<u> Ware resultaten </u>:

De pagina wordt omhoog geschoven telkens als a **verfrist** knoop wordt geklikt. De naam van het product komt niet voor in de juiste sectie.

## Oplossing

Een alternerende actie is de gebruiker Admin kan de Activiteiten van **Klant** bijwerken door de **knoop van de Veranderingen van de Update** bij de bodem van sidebar te klikken. Het probleem wordt opgelost in de Adobe Commerce 2.4.1-patch.

![ mceclip0.png ](assets/mceclip0.png)

## Gerelateerde lezing

* [Bekende uitgave van Adobe Commerce 2.4.0: Betalingsmethoden voor Braintree worden niet weergegeven bij de afhandeling van meerdere adressen](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Aanmaak van verzendlabels Bekend probleem in Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: onbewerkte weergave van berichtgegevens op winkel](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Export Tax Rates werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: &quot;Selecties toevoegen aan mijn winkelwagentje&quot; werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
