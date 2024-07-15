---
title: Aanmaak van verzendlabels Bekend probleem in Adobe Commerce 2.4.0
description: Dit artikel bevat een patch voor een bekende Adobe Commerce 2.4.0-uitgave, waarbij geen verzendlabel kan worden gemaakt.
exl-id: 722689d9-0c90-4a9d-8449-e93c6585b7c3
feature: Orders, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Aanmaak van verzendlabels Bekend probleem in Adobe Commerce 2.4.0

Dit artikel bevat een patch voor een bekende Adobe Commerce 2.4.0-uitgave, waarbij geen verzendlabel kan worden gemaakt.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.0
* Adobe Commerce over cloudinfrastructuur 2.4.0

## Probleem

<u> Eerste vereisten </u>: creeer een orde gebruikend FedEx, DHL, UPS, of USPS het verschepen methode.

### Scenario 1: Een label maken bij het toevoegen van een verzending

<u> Stappen om te reproduceren:</u>

1. Open de geplaatste orde in Admin, onder **Verkoop** > **Orden**.
1. Klik de **Schip** knoop. De **Nieuwe Verzending** pagina opent.

<u> Verwacht resultaat:</u>

**creeer het Verschepen van Etiket** checkbox wordt getoond in de bodem van de pagina.

<u> Ware resultaat:</u>

**creeer het Verschepen van Etiket** checkbox wordt niet getoond.

### Scenario 2: Een label maken voor bestaande verzending

<u> Stappen om te reproduceren:</u>

1. Open de geplaatste orde in Admin, onder **Verkoop** > **Orden**.
1. Klik de **Schip** knoop. De **Nieuwe Verzending** pagina opent.
1. Klik **voorleggen Verzending** knoop. Er wordt een verzending gemaakt.
1. Open de nieuwe verzending.
1. Klik **creeer het Verschepen van Etiket** knoop. Het **leidt tot de dialoog van Pakketten** opent.

<u> Verwacht resultaat:</u>

**voegt Producten aan de knoop van het Pakket** op **toe leidt tot Pakketten** modale venstervertoningen van het venster met orde punten.

<u> Ware resultaat:</u>

**creeer Pakketten** modaal venster niet behoorlijk wordt getoond, is het niet mogelijk om orde punten aan de verzending toe te voegen.

## Oplossing

Pas de patch toe die in dit artikel is opgenomen.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[MC-35514-2.4.0-CE-composer-2.patch](assets/MC-35514-2.4.0-CE-composer-2.patch.zip)

Het flard is ook beschikbaar voor download in zowel, `.git` als `.composer`, formaten op [ de Downloads van Adobe Commerce ](https://magento.com/tech-resources/download) pagina, onder **Patches** in de linkerkolomnavigatie. Zoeken naar MC-35514-patch.

### Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce on cloud Infrastructure versie 2.4.0
* Adobe Commerce on-premisse versie 2.4.0

## Hoe de pleister aanbrengen

Zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies wordt verstrekt.

## Bijgevoegde bestanden
