---
title: Problemen met gereedheid voor componentafhankelijkheid
description: Dit artikel biedt oplossingen voor conflicten met componentafhankelijkheid.
exl-id: e0865226-2aaf-4bdd-8c28-28f32f38ce0c
feature: Configuration
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Problemen met gereedheid voor componentafhankelijkheid

Dit artikel biedt oplossingen voor conflicten met componentafhankelijkheid.

## Conflicten met componentafhankelijkheid oplossen {#resolve-component-dependency-conflicts}

We raden u aan de volgende oplossingen in de aangegeven volgorde te kiezen:

1. [Conflicterende afhankelijkheden](#trouble-depend-conflict)
1. [Problemen met bestandssysteemmachtigingen](#trouble-depend-permission)
1. [De status van Componentafhankelijke controle verandert nooit](#trouble-depend-state)

### Conflicterende afhankelijkheden {#trouble-depend-conflict}

Het bericht *wij ontdekten conflicterende componentengebiedsdelen* tonen als Composer niet kan bepalen welke componenten om te installeren of bij te werken. Om componentenafhankelijkheidskwesties op te lossen, zou u een technische persoon moeten zijn die grondig begrijpt hoe Composer werkt.

Hier volgt een voorbeeld van een foutbericht:

```bash
We found conflicting component dependencies.
 You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
 We've detected conflicts with the following packages:
 - magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

>[!NOTE]
>
>Het bericht dat u ziet, zal waarschijnlijk anders zijn.

Verwijs naar [ Conflicterende componentengebiedsdelen voor een oplossing ](/help/troubleshooting/miscellaneous/conflicting-component-dependencies.md) in onze basis van steunkennis.

## Problemen met bestandssysteemmachtigingen {#trouble-depend-permission}

Als de eigenaar van het Adobe Commerce-bestandssysteem niet de machtigingen heeft om naar mappen in het Adobe Commerce-bestandssysteem te schrijven, wordt een bericht weergegeven dat lijkt op het volgende:

```bash
file_put_contents(/var/www/html/magento2/var/composer_home/cache/repo/https---
packagist.org/provider-doctrine$instantiator.json): failed to open stream: Permission denied
```

Zorg ervoor u de toestemmingen van het dossiersysteem zoals besproken in het artikel [ Overzicht van eigendom en toestemmingen ](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html) in onze ontwikkelaarsdocumentatie plaatst.

## De status van Componentafhankelijke controle verandert nooit {#trouble-depend-state}

In sommige gevallen verandert de status van Componentafhankelijke controle niet, zelfs niet nadat u problemen hebt verholpen. In dat geval kunt u bestanden met de namen `<magento_root>/var/.update_cronjob_status` en `<magento_root>/var/.setup_cronjob_status` verwijderen of de naam ervan wijzigen en probeert u Componentbeheer opnieuw uit te voeren.

Als u de naam van deze bestanden wijzigt of deze bestanden verwijdert, wordt Componentbeheer gedwongen de controles opnieuw uit te voeren.
