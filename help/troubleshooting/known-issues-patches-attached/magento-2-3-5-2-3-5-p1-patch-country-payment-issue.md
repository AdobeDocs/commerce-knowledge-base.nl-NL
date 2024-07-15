---
title: "Adobe Commerce 2.3.5, 2.3.5-p1 patch: country payment issue"
description: Deze patch verhelpt een probleem in Adobe Commerce dat er in de workflow voor het uitchecken van winkels geen betalingsmethode werd weergegeven die voor bepaalde landen is ingeschakeld, behalve voor Klarna en Amazon Pay.
exl-id: e205e35e-9ffe-4826-b951-3a3caf1e0621
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Adobe Commerce 2.3.5, 2.3.5-p1-patch: probleem met landbetaling

Deze patch verhelpt een probleem in Adobe Commerce dat er in de workflow voor het uitchecken van winkels geen betalingsmethode werd weergegeven die voor bepaalde landen is ingeschakeld, behalve voor Klarna en Amazon Pay.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur 2.3.5 en 2.3.5-p1
* Adobe Commerce op locatie 2.3.5 en 2.3.5-p1

## Probleem

Wanneer een winkel Amazon Pay heeft en een andere betaling aan verschillende landen is toegewezen, en wanneer een van die landen en betalingsmethoden is geselecteerd, zijn de knoppen voor de betalingsmethode en de plaatsingsopdracht niet zichtbaar.

Een webpagina vernieuwen is een tijdelijke oplossing voor de uitgave.

Om deze kwestie op te lossen en de fout te verwijderen, hebben wij a [ flard ](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip) gecreeerd.

<u> Eerste vereisten </u>:

* Er wordt een eenvoudig product gemaakt.
* **Controle/Geldorde** wordt toegelaten slechts voor specifieke landen (bij **Opslag** > **Configuratie** > **Verkoop** > **de Methoden van de Betaling**).

* Voorbeeld: Betaling uit landen van toepassing = specifieke landen
* Voorbeeld: Betaling uit specifieke landen = Verenigd Koninkrijk

<u> Stappen om </u> te reproduceren:

1. Ga naar de Storefront als gast.
1. Voeg een eenvoudig product toe aan het winkelwagentje.
1. Ga naar Afhandeling.
1. Vul het formulier met geldige gegevens.

   * Land = *Verenigde Staten*

1. Selecteer het verschepen tarief en klik **daarna**.

   * De betalingsstap is geopend.
   * Er zijn geen betalingen beschikbaar.
   * Bericht: **Geen beschikbare methode van de Betaling.**
   * Er is geen **knoop van de Orde van de Plaats**.

1. Ga terug naar de **Verschepende Stap** en verander de waarde aan:

   * Land = *Verenigd Koninkrijk*

1. Selecteer het verschepen tarief en klik **daarna**.

<u> Verwacht resultaat </u>:

De stap Betaling wordt geopend.

* **Onder rembours** verschijnt.
* **Controle/Geldorde** verschijnt.
* De **knoop van de Orde van de Plaats** verschijnt.

<u> Werkelijk resultaat </u>:

De stap Betaling wordt geopend.

* Er zijn geen betalingen beschikbaar.
* Bericht: *Geen beschikbare methode van de Betaling.*
* Er is geen **knoop van de Orde van de Plaats**.

## Oplossing

[ pas het flard ](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip) hieronder toe.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[BUNDLE-2546\_EE\_2.3.5-p1.composer.patch downloaden](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip)

### Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce op cloudinfrastructuur 2.3.5 en 2.3.5-p1
* Adobe Commerce op locatie 2.3.5 en 2.3.5-p1

De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce 2.3.4-p2 - 2.2.6

## Hoe de pleister aanbrengen

Zie [ hoe te om een componentenflard toe te passen die door Adobe Commerce ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze steunkennisbasis voor instructies wordt verstrekt.

## Bijgevoegde bestanden
