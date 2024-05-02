---
title: Site kan niet worden geladen omdat de onderhoudsmodus ingeschakeld blijft
description: "Dit artikel bevat een oplossing voor het geval uw site niet wordt geladen omdat de onderhoudsmodus ingeschakeld blijft of niet automatisch is uitgeschakeld. U ontvangt mogelijk een foutbericht: *Service tijdelijk niet beschikbaar De server kan uw verzoek tijdelijk niet uitvoeren vanwege onderhouds- of capaciteitsproblemen.*"
exl-id: 77e01588-e135-4d24-a0c4-1a6ee123f4a8
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Site kan niet worden geladen omdat de onderhoudsmodus ingeschakeld blijft

Dit artikel bevat een oplossing voor het geval uw site niet wordt geladen omdat de onderhoudsmodus ingeschakeld blijft of niet automatisch is uitgeschakeld. U ontvangt mogelijk een foutbericht: *Service tijdelijk niet beschikbaar De server kan uw verzoek tijdelijk niet uitvoeren vanwege onderhouds- of capaciteitsproblemen.*

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

Raadpleeg voor meer informatie over het gebruik van de onderhoudsmodus [Onderhoudsmodus in- of uitschakelen](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=maintenance%20mode) in onze ontwikkelaarsdocumentatie.
