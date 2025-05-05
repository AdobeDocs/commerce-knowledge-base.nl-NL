---
title: Site kan niet worden geladen omdat de onderhoudsmodus ingeschakeld blijft
description: 'Dit artikel bevat een oplossing voor het geval uw site niet wordt geladen omdat de onderhoudsmodus ingeschakeld blijft of niet automatisch is uitgeschakeld. U ontvangt mogelijk een foutbericht: *Service tijdelijk niet beschikbaar De server kan uw verzoek tijdelijk niet uitvoeren vanwege onderhouds- of capaciteitsproblemen.*'
exl-id: 77e01588-e135-4d24-a0c4-1a6ee123f4a8
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Site kan niet worden geladen omdat de onderhoudsmodus ingeschakeld blijft

Dit artikel bevat een oplossing voor het geval uw site niet wordt geladen omdat de onderhoudsmodus ingeschakeld blijft of niet automatisch is uitgeschakeld. U kunt een foutenmelding ontvangen: *de Dienst tijdelijk niet beschikbaar is De server is tijdelijk niet in staat om uw verzoek wegens onderhoudsonderbreking of capaciteitsproblemen te onderhouden.*

## Betrokken versies en producten

* Adobe Commerce op cloud-infrastructuur 2.2.x, 2.3.x
* Adobe Commerce op locatie 2.2.x, 2.3.x

## Probleem

De onderhoudsmodus maakt deel uit van het implementatieproces. Nochtans, als het automatisch is toegelaten en niet onbruikbaar gemaakt, of de handelaars toegelaten onderhoudswijze manueel en vergat om onbruikbaar te maken, kan het een ontbroken plaatsing veroorzaken.

## Oorzaak

Als de onderhoudsmodus ingeschakeld is, kan de site niet worden geladen.

## Oplossing

Om de huidige status van de onderhoudswijze te controleren, stel het volgende bevel van CLI in werking:

```
bin/magento maintenance:status
```

Om onderhoudswijze onbruikbaar te maken, stel het volgende bevel in CLI in werking:

```
bin/magento maintenance:disable
```

## Verwante lezing

Leren wanneer om onderhoudswijze te gebruiken, verwijs naar [ toelaten of onderhoudswijze ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in onze ontwikkelaarsdocumentatie onbruikbaar maken.
