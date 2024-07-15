---
title: Implementatielogbestand controleren als in de gebruikersinterface van Cloud een fout met een 'log snipped' is opgetreden
description: Dit artikel biedt een oplossing voor het probleem waarbij de gebruikersinterface van de Adobe Commerce on cloud-infrastructuur het *log snipped weergeeft omdat het te lang* foutbericht was toen werd geprobeerd het implementatielogboek in de gebruikersinterface van het cloudproject weer te geven.
exl-id: 04d28741-72c1-4722-be46-425fe136b9a6
feature: Cloud, Deploy, Logs, Paas
role: Developer
source-git-commit: 71bec5b99063d771982f6dcab111b9e5a4aaec69
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Het controleren plaatsingslogboek als de wolk UI *logboek heeft dat* fout knipte

Dit artikel verstrekt een oplossing voor de kwestie waar Adobe Commerce op de interface van de wolkeninfrastructuur het *ontsponnen logboek toont omdat het* foutenbericht te lang was toen het proberen om het plaatsingslogboek op het wolkenproject UI te bekijken. (Is niet op de [ Console van Adobe Commerce Cloud ](https://console.adobecommerce.com/) van toepassing.)

## Betrokken producten

Adobe Commerce op cloudinfrastructuur (alle ondersteunde versies)

## Probleem

Wanneer het proberen om het plaatsingslogboek op het wolkenproject UI te bekijken, toont Adobe Commerce op de interface van de wolkeninfrastructuur het volgende foutenbericht: *logboek dat omdat het te lang* was.

## Stappen om te reproduceren

1. Ga naar het Project URL en klik op de **Status** van de plaatsing in kwestie.
1. Als het logboek te lang is om in UI te worden getoond, zal het het foutenbericht tonen: *het logboek dat wordt gesneld omdat het te lang* was.

## Oorzaak

Merk op dat het logboek dat in UI wordt getoond niet als bron van waarheid zou moeten worden behandeld, vooral als u vindt dat de plaats niet of behoorlijk werkt nadat de plaatsing met een status van Succes werd vermeld. U moet ook controleren met de logboeken op de server. Verwijs naar [ Mening en beheer logboeken ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) in onze ontwikkelaarsdocumentatie.

## Oplossing

1. Zorg ervoor dat u [ CLI van de Wolk van het Magento ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html) geïnstalleerd in uw lokale milieu hebt.
1. Voer de volgende opdracht uit:

   ```bash
   magento-cloud activity -p <project id> -e <environment>
   ```

1. De uitvoer wordt als volgt weergegeven:

   ```bash
   Activities on the project <project name> (project id), environment <environment>:
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | ID            | Created                   | Description                         | Progress | State    | Result  |
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | l5wgwmzwrsskg | 2021-06-01T08:18:02-07:00 | ABC merged Integration into Staging | 100%     | complete | success |
   | raah5xrhqz3wg | 2021-06-01T08:07:18-07:00 | XYZ pushed to Integration           | 100%     | complete | failure |
   ```

1. Kopieer de activiteit-id van de betrokken implementatie en voer de opdracht vervolgens uit:

   ```bash
   magento-cloud activity:log <activity ID> -p <project id> -e <environment>
   ```

   Voorbeeld om het logboek van de ontbroken plaatsing te onderzoeken:

   ```bash
   magento-cloud activity:log raah5xrhqz3wg -p <project id> -e <environment>
   ```

## Verwante lezingen in onze ontwikkelaarsdocumentatie:

* [ Adobe Commerce op wolkeninfrastructuur > bouwt en stelt ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) op
* [ Adobe Commerce op wolkeninfrastructuur > Logboeken van de Mening en van het beheer ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)
