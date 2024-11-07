---
title: Foutbericht bij het toevoegen van sites aan Beveiligingsscan
description: Dit artikel biedt mogelijke oplossingen voor het probleem wanneer een gebruiker geen sites kan toevoegen aan de [Commerce Security Scan] (https://account.magento.com/scanner/dashboard/).
exl-id: 8d000ca4-b977-432d-bb26-6ea320067a40
feature: Cache, Compliance, Console, Security
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Foutbericht bij het toevoegen van sites aan Beveiligingsscan

Dit artikel verstrekt mogelijke oplossingen voor de kwestie wanneer een gebruiker geen plaatsen in het [ Scannen van de Veiligheid van Commerce ](https://account.magento.com/scanner/dashboard/) kan toevoegen.

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden en -versies)
* Magento Open Source

## Probleem

De gebruiker kan geen plaatsen in het [ Scannen van de Veiligheid van Commerce ](https://account.magento.com/scanner/dashboard/) toevoegen. Het volgende foutenbericht verschijnt wanneer het proberen om een plaats toe te voegen: *kan geen plaats voor het aftasten voorleggen.*

## Oplossing

1. Zorg ervoor dat de volgende IP adressen niet op havens 80 en 443 worden geblokkeerd:
   * 52 87 98 44
   * 34 196 167 176
   * 3 218 25 102

1. De bevestigingscode is tijdgevoelig. Als meer dan 30 minuten zijn overgegaan nadat **plaats** verbinding werd geklikt toevoegt, is de code waarschijnlijk verlopen.
1. Vergeet niet cache op te schonen en ervoor te zorgen dat de validatiecode in de brontekst van de startpagina wordt weergegeven. De bevestigingscode moet worden geïnjecteerd volgens de HTML-opmaakspecificaties: HTML-commentaar kan in de hoofdtekst van de pagina worden geïnjecteerd (we raden aan het in de voettekstsectie te plaatsen); de META-tag mag alleen in de hoofdsectie staan.
1. Alvorens **te klikken verifieer de code van de Bevestiging**, open de de ontwikkelaarsconsole van browser, klik het **3} lusje van het Netwerk {en controleer de reactie van magento.com.** De waarde moet HTTP 200 (OK) zijn en de hoofdtekst van de reactie moet een JSON-object bevatten.
1. Wanneer de antwoordcode HTTP 200 is en de hoofdtekst van de reactie een JSON-object is en de waarde van de eigenschap `verified` `false` is, betekent dit dat de code niet op de pagina wordt gevonden. De eigenschapwaarde `details` moet de uitleg bevatten. Als de winkel bijvoorbeeld een zelfondertekend SSL-certificaat gebruikt, treedt er waarschijnlijk een verbindingsfout op.

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

* [ Scannen van de Veiligheid ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) in onze gebruikersgids.
