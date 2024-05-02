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

<u>Vereisten</u>: maak een bestelling met de verzendmethode FedEx, DHL, UPS of USPS.

### Scenario 1: Een label maken bij het toevoegen van een verzending

<u>Stappen om te reproduceren:</u>

1. Open de geplaatste order in de beheerdersruimte, onder **Verkoop** > **Orders**.
1. Klik op de knop **Schip** knop. De **Nieuwe verzending** pagina wordt geopend.

<u>Verwacht resultaat:</u>

De **Verzendlabel maken** het selectievakje wordt onder aan de pagina weergegeven.

<u>Werkelijk resultaat:</u>

De **Verzendlabel maken** het selectievakje wordt niet weergegeven.

### Scenario 2: Een label maken voor bestaande verzending

<u>Stappen om te reproduceren:</u>

1. Open de geplaatste order in de beheerdersruimte, onder **Verkoop** > **Orders**.
1. Klik op de knop **Schip** knop. De **Nieuwe verzending** pagina wordt geopend.
1. Klik op de knop **Verzending verzenden** knop. Er wordt een verzending gemaakt.
1. Open de nieuwe verzending.
1. Klik op de knop **Verzendlabel maken** knop. De **Pakketten maken** wordt geopend.

<u>Verwacht resultaat:</u>

De **Producten toevoegen aan pakket** op de knop **Pakketten maken** in een modaal venster worden velden met volgordeitems weergegeven.

<u>Werkelijk resultaat:</u>

De **Pakketten maken** modaal venster wordt niet correct weergegeven, het is niet mogelijk om orde punten aan de verzending toe te voegen.

## Oplossing

Pas de patch toe die in dit artikel is opgenomen.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[MC-35514-2.4.0-CE-composer-2.patch](assets/MC-35514-2.4.0-CE-composer-2.patch.zip)

De patch is ook beschikbaar voor beide toepassingen, `.git` en `.composer`, indelingen op [Adobe Commerce-downloads](https://magento.com/tech-resources/download) pagina, onder **Patches** in de linkerkolomnavigatie. Zoeken naar MC-35514-patch.

### Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce on cloud Infrastructure versie 2.4.0
* Adobe Commerce on-premisse versie 2.4.0

## Hoe de pleister aanbrengen

Zie [Hoe een door Adobe geleverde componentpleister aanbrengen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies.

## Bijgevoegde bestanden
