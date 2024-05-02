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

<u>Stappen om te reproduceren</u>:

1. Ga naar de **Deelvenster Beheer** > **Verkoop** > **Orders**.
1. Klik op de knop **Nieuwe volgorde maken** knop.
1. Selecteer de klant die u hebt gemaakt.
1. Ga naar de winkel als de nieuwe klant.
1. Ga naar de **Product** pagina. Klik op de knop **Vernieuwen** op de knop **Onlangs bekeken producten** deel van **Activiteiten van de klant**.
1. Ga terug naar de winkel.
1. Plaats een bestelling met de gemaakte producten.
1. Ga terug naar de **Deelvenster Beheer** en klik op de knop **Vernieuwen** van de **Laatst bestelde objecten** deel van **Activiteiten van de klant**.
1. Ga terug naar de winkel. Het gemaakte product toevoegen aan de **Vergelijkingslijst**.
1. Ga terug naar de **Deelvenster Beheer**. Klik op de knop **Vernieuwen** van de **Producten in vergelijkingslijst** deel van **Activiteiten van de klant**.
1. Ga terug naar de winkel.
1. Het gemaakte product verwijderen uit de **Vergelijkingslijst**.
1. Ga terug naar de **Deelvenster Beheer**.
1. Klik op de knop **Vernieuwen** van de **Onlangs vergeleken producten** deel van **Activiteiten van de klant**.
1. Ga terug naar de winkel.

<u>Verwachte resultaten</u>:

De naam van het product moet in de **Onlangs bekeken producten**, **Laatst bestelde objecten**, **Producten in vergelijkingslijst**, en **Onlangs vergeleken producten** sectie.

<u>Werkelijke resultaten</u>:

De pagina wordt elke keer dat een **Vernieuwen** wordt geklikt. De naam van het product komt niet voor in de juiste sectie.

## Oplossing

Een oplossing is dat de Admin-gebruiker de update kan uitvoeren **Activiteiten van de klant** door op de knop **Wijzigingen bijwerken** onder aan de zijbalk. Het probleem wordt opgelost in de Adobe Commerce 2.4.1-patch.

![mceclip0.png](assets/mceclip0.png)

## Gerelateerde lezing

* [Bekende uitgave van Adobe Commerce 2.4.0: Betalingsmethoden voor Braintree worden niet weergegeven bij de afhandeling van meerdere adressen](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Aanmaak van verzendlabels Bekend probleem in Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: onbewerkte weergave van berichtgegevens op winkel](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Export Tax Rates werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: &quot;Selecties toevoegen aan mijn winkelwagentje&quot; werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
