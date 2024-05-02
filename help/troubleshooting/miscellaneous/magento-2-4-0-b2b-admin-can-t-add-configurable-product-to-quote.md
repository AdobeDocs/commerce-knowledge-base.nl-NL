---
title: Adobe Commerce 2.4.0 B2B Admin kan geen configureerbaar product toevoegen om te citeren
description: In dit artikel wordt gesproken over een bekend probleem in Commerce Admin bij het beheren van een B2B-offerte. Het is niet mogelijk een configureerbaar product door **SKU** aan het aanhalingsteken toe te voegen. Wanneer u op de knop **Toevoegen aan offerte** klikt, blijft de bewerkingspagina **Offerte** vastzitten en kunt u het product niet configureren en wijzigingen opslaan. Dit probleem doet zich ook voor in Admin wanneer u een product van **SKU** aan een bestelling toevoegt of een product van **SKU** in **Advanced Checkout** (**Admin*** gt; **Klanten*** gt; **Alle Klanten*** gt; **Klant geeft** B uit; **Winkelwagen beheren*). Dit probleem wordt opgelost in een patch voor Adobe Commerce 2.4.1.
exl-id: 73f7231b-b496-4250-b9e2-29427c772d56
feature: Admin Workspace, B2B, Catalog Management, Configuration, Products, Quotes
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B Admin kan geen configureerbaar product toevoegen om te citeren

In dit artikel wordt gesproken over een bekend probleem in Commerce Admin bij het beheren van een B2B-offerte. Het is niet mogelijk om een configureerbaar product toe te voegen door **SKU** aan het citaat. Wanneer u op de knop **Toevoegen aan offerte** de **Offerte** Het laden van de pagina blijft ongewijzigd en u kunt het product niet configureren en wijzigingen opslaan. Dit probleem doet zich ook voor in Admin wanneer u een product toevoegt door **SKU** aan een bestelling, of een product toevoegen door **SKU** in **Geavanceerde afhandeling** (**Beheerder** > **Klanten** > **Alle klanten** > **Klant bewerken** > **Winkelwagentje beheren**). Dit probleem wordt opgelost in een patch voor Adobe Commerce 2.4.1.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.0
* Adobe Commerce over cloudinfrastructuur 2.4.0

## Probleem

<u>Voorwaarden</u>

* Adobe Commerce 2.4.0 is geïnstalleerd.
* B2B is geïnstalleerd.
* B2B-functies instellen op **Bedrijf inschakelen =**  *Ja* , **Gedeelde catalogus inschakelen =**  *Nee* , en **B2B-offerte inschakelen =**  *Ja*.
* Maak een klantenaccount.
* Maak een bedrijfsaccount met de eerder gemaakte klant als bedrijfsbeheerder.
* Een eenvoudig product maken (bijvoorbeeld: naam &amp; **SKU** = TEST SIMPLE 1) die niet is toegewezen aan **Standaard (algemeen)**.
* Laat de bedrijfsbeheerder een prijsopgave aanvragen met behulp van het hierboven gemaakte eenvoudige product (bijvoorbeeld: TEST SIMPLE 1).

<u>Stappen om te reproduceren</u>

1. Ga naar het deelvenster Commerce Admin.
1. Ga naar **Verkoop > Aanhalingstekens**.
1. Open de **Offerte**.
1. Klik op de knop **Product toevoegen door SKU** knop.
1. Voer de **SKU** van een ander product (bijvoorbeeld: TEST SIMPLE 2) in het **SKU invoeren** invoerveld.
1. Geef een geldig aantal op in de **Aantal** invoerveld.
1. Klik op de knop **Toevoegen aan offerte** knop.

<u>Verwachte resultaten</u>

* De **Producten niet toegevoegd aan het Citaat** raster, met de naam en **SKU** van het gemaakte product wordt weergegeven zoals u had verwacht.
* Nadat het product is geconfigureerd, kan Admin het toevoegen aan de **Offerte** door op de knop **Producten toevoegen aan offerte** zoals verwacht.

<u>Werkelijke resultaten</u>

* De **Producten niet toegevoegd aan het Citaat** raster, met de naam en **SKU** van het gemaakte product wordt niet weergegeven.
* De **Offerte** pagina blijft geladen.

## Aanbeveling

Er is momenteel geen oplossing voor dit probleem met B2B Offertebewerking, maar voor Order en Shopping Cart-beheer is het mogelijk producten te selecteren in het menu **Lijst met producten** in plaats van ze toe te voegen door **SKU**. Voor Adobe Commerce 2.4.1 is een patch beschikbaar om het probleem op te lossen. Deze patch is gepland voor release in Q4 2020.

## Gerelateerde lezing

* [Bekende uitgave van Adobe Commerce 2.4.0: Vernieuwen van activiteiten van de Klant werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Onbewerkte weergave van berichtgegevens op Storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: belastingtarieven voor export werken niet](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: weergavefout voor bestellingen](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
