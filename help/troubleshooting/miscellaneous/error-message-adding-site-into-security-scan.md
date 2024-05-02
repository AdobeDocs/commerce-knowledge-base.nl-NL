---
title: Foutbericht bij het toevoegen van sites aan Beveiligingsscan
description: Dit artikel biedt mogelijke oplossingen voor het probleem wanneer een gebruiker geen sites kan toevoegen aan de [Commerce Security Scan] (https://account.magento.com/scanner/dashboard/).
exl-id: 8d000ca4-b977-432d-bb26-6ea320067a40
feature: Cache, Compliance, Console, Security
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Foutbericht bij het toevoegen van sites aan Beveiligingsscan

Dit artikel biedt mogelijke oplossingen voor de kwestie wanneer een gebruiker geen sites kan toevoegen aan de [Commerce Security Scan](https://account.magento.com/scanner/dashboard/).

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden en -versies)
* Magento Open Source

## Probleem

Gebruiker kan geen sites toevoegen aan de [Commerce Security Scan](https://account.magento.com/scanner/dashboard/). Het volgende foutbericht wordt weergegeven wanneer u een site probeert toe te voegen: *Kan site niet verzenden voor scannen.*

## Oplossing

1. Zorg ervoor dat de volgende IP adressen niet op havens 80 en 443 worden geblokkeerd:
   * 52 87 98 44
   * 34 196 167 176
   * 3 218 25 102

1. De bevestigingscode is tijdgevoelig. Indien meer dan 30 minuten voorbij zijn gegaan na de **Site toevoegen** Er is op de koppeling geklikt, de code is waarschijnlijk verlopen.
1. Vergeet niet cache op te schonen en ervoor te zorgen dat de validatiecode in de brontekst van de startpagina wordt weergegeven. De bevestigingscode moet worden geïnjecteerd volgens de HTML-opmaakspecificaties: HTML-commentaar kan in de hoofdtekst van de pagina worden geïnjecteerd (we raden aan het in de voettekstsectie te plaatsen); de META-tag mag alleen in de hoofdsectie staan.
1. Voordat u klikt **Bevestigingscode verifiëren**, opent u de ontwikkelaarsconsole van de browser en klikt u op de knop **Netwerk** en bekijk het antwoord van magento.com. De waarde moet HTTP 200 (OK) zijn en de hoofdtekst van de reactie moet een JSON-object bevatten.
1. Als de responscode HTTP 200 is en de hoofdtekst van de reactie een JSON-object en de `verified` eigenschapswaarde is `false`, betekent dit dat de code niet op de pagina is gevonden. De `details` De waarde van de eigenschap moet de uitleg bevatten. Als de winkel bijvoorbeeld een zelfondertekend SSL-certificaat gebruikt, treedt er waarschijnlijk een verbindingsfout op.

Voer de volgende stappen uit als u nog steeds geen sites kunt toevoegen:

1. Plaats nog een HTML-opmerking op de pagina:

   ```HTML
   <!-- MAGEID:Your magento.com ID, EMAIL:your email address -->
   ```

1. Stuur een ondersteuningsticket en geef de volgende informatie:
   * URL Adobe Commerce-winkel
   * MAGEID + Magento.com-account
   * Voornaam + Achternaam
   * Bedrijfsnaam
   * E-maillijst met door komma&#39;s gescheiden meldingen

## Gerelateerde lezing

* [Beveiligingsscan](https://docs.magento.com/user-guide/magento/security-scan.html) in onze gebruikershandleiding.
