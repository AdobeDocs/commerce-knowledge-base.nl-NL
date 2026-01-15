---
title: Adobe Commerce 2.4.0 B2B Admin kan geen configureerbaar product toevoegen om te citeren
description: In dit artikel wordt gesproken over een bekend probleem in Commerce Admin bij het beheren van een B2B-offerte. Het is niet mogelijk een configureerbaar product door **SKU** aan het aanhalingsteken toe te voegen. Wanneer u op de knop **Toevoegen aan offerte** klikt, blijft de bewerkingspagina **Offerte** vastzitten en kunt u het product niet configureren en wijzigingen opslaan. Dit probleem doet zich ook voor in Admin wanneer u een product van **SKU** aan een bestelling toevoegt of een product van **SKU** in **Advanced Checkout** (**Admin**** amp;gt; **Klanten**** amp;gt; **Alle Klanten*** amp;gt; **Klant bewerken******). Dit probleem wordt opgelost in een patch voor Adobe Commerce 2.4.1.
exl-id: 73f7231b-b496-4250-b9e2-29427c772d56
feature: Admin Workspace, B2B, Catalog Management, Configuration, Products, Quotes
role: Developer
source-git-commit: 05297c82b292b8ccc88018c58e991bd3a32d6ffa
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B Admin kan geen configureerbaar product toevoegen om te citeren

Dit artikel spreekt over een bekende kwestie in Commerce Admin wanneer het beheren van een Citaat B2B, is het niet mogelijk om een configureerbaar product door **SKU** aan het citaat toe te voegen. Wanneer het klikken van **toevoegt aan de knoop van het Citaat**, geeft het **Citaat** pagina uit is geplakt ladend, en u kunt niet het product vormen en veranderingen bewaren. Deze kwestie komt ook in Admin voor wanneer het toevoegen van een product door **SKU** aan een orde, of het toevoegen van een product door **SKU** in **Geavanceerde Controle** (**Admin** > **Klanten** > **Alle Klanten** > **geeft** > **leidt Winkelwagentje**). Dit probleem wordt opgelost in een patch voor Adobe Commerce 2.4.1.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.0
* Adobe Commerce over cloudinfrastructuur 2.4.0

## Probleem

<u> Voorwaarden </u>

* Adobe Commerce 2.4.0 is geïnstalleerd.
* B2B is geïnstalleerd.
* Plaats B2B eigenschappen aan **laat Bedrijf toe =** *ja*, **laat Gedeelde Catalogus toe =** *Nr*, en **laat B2B Citaat toe =** *ja*.
* Maak een klantenaccount.
* Maak een bedrijfsaccount met de eerder gemaakte klant als bedrijfsbeheerder.
* Creeer een eenvoudig product (Voorbeeld: naam &amp; **SKU** = TEST EENVOUDIGE 1) die niet aan **Gebrek (Algemeen)** wordt toegewezen.
* Laat de bedrijfsbeheerder een prijsopgave aanvragen met behulp van het hierboven gemaakte eenvoudige product (bijvoorbeeld: TEST SIMPLE 1).

<u> Stappen om te reproduceren </u>

1. Ga naar het deelvenster Commerce Admin.
1. Ga naar **Verkoop > Citaten**.
1. Open het **Citaat**.
1. Klik **toevoegen Product door SKU** knoop.
1. Ga het **SKU** van een ander (Voorbeeld: TEST EENVOUDIGE 2) product in **binnen SKU** inputgebied.
1. Ga één of andere geldige hoeveelheid in het **Qty** inputgebied in.
1. Klik **toevoegen aan Citaat** knoop.

<u> Verwachte resultaten </u>

* De **Producten die niet aan het 1&rbrace; net van het Citaat &lbrace;worden toegevoegd, die de naam en** SKU **van het gecreeerde product bevatten, verschijnt zoals verwacht.**
* Nadat het product wordt gevormd, kan Admin het aan het **Citaat** toevoegen door **te klikken voegt Producten aan Citaat** knoop toe, zoals verwacht.

<u> Ware resultaten </u>

* De **Producten die niet aan het 1&rbrace; net van het Citaat &lbrace;worden toegevoegd, die de naam en** SKU **van het gecreeerde product bevatten, verschijnen niet.**
* De **Citaat** pagina wordt geplakt ladend.

## Aanbeveling

Momenteel, is er geen alternerende actie voor deze kwestie met B2B Citaat het uitgeven, maar voor de Orde en het Shopping Beheer van de Kaart, is het mogelijk om producten van de **Lijst van Producten** in plaats van het toevoegen van hen door **SKU** te selecteren. Voor Adobe Commerce 2.4.1 is een patch beschikbaar om het probleem op te lossen. Deze patch is gepland voor release in Q4 2020.

