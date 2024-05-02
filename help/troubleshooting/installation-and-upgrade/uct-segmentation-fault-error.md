---
title: Fouten met upgradecompatibiliteitsgereedschappen oplossen
description: In dit artikel worden de fouten uitgelegd die u kunt ervaren tijdens het gebruik van het gereedschap Compatibiliteit bijwerken. Het artikel bevat oplossingen voor deze fouten zodat u het gereedschap kunt uitvoeren.
exl-id: 1cce1146-942e-46cb-a395-8da9e472cd39
feature: Customer Service, Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Fouten met upgradecompatibiliteitsgereedschappen oplossen

In dit artikel worden de fouten uitgelegd die u kunt ervaren tijdens het gebruik van het gereedschap Compatibiliteit bijwerken. Het artikel bevat oplossingen voor deze fouten zodat u het gereedschap kunt uitvoeren.

## Betrokken producten en versies

* [Compatibiliteit upgraden](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html) is vanaf 2.3.0 compatibel met Adobe Commerce-versies.

## Fout in segmentfout

<u>Oorzaak</u>:

Wanneer twee modules de zelfde naam hebben, toont het Hulpmiddel van de Verenigbaarheid van de Verbetering een fout van de segmenteringsfout.

<u>Oplossing</u>:

Om deze fout te vermijden, wordt aanbevolen het pad naar de module als argument op te geven:

```bash
bin/uct upgrade:check --current-version=2.4.4 path/to/the/module
```

>[!WARNING]
>
> Het gereedschap Compatibiliteit bijwerken kan de codebase mogelijk niet analyseren als deze cyclische afhankelijkheid tussen methoden bevat.

## Lege uitvoer

<u>Stappen om te reproduceren</u>:

1. Indien na het uitvoeren van deze opdracht:

   ```bash
   bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
   ```

1. De enige uitvoer is `Upgrade compatibility tool`:

   ```terminal
   bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
   Upgrade compatibility tool
   ```

<u>Oorzaak</u>:

De waarschijnlijke oorzaak is een PHP geheugenbeperking.

Er zijn twee mogelijke oplossingen om deze PHP geheugenbeperking te voorkomen.

<u>Oplossing 1</u>:

De geheugenbeperking overschrijven door deze in te stellen `memory_limit` tot `-1`:

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

>[!NOTE]
>
> De `M2_VERSION` Dit is de Adobe Commerce-doelversie die u wilt vergelijken met uw Adobe Commerce-exemplaar.

<u>Oplossing 2</u>:

De `-m` Met het gereedschap Compatibiliteit upgraden kunt u elke specifieke module afzonderlijk analyseren om te voorkomen dat er twee modules met dezelfde naam in uw Adobe Commerce-instantie voorkomen.

Met deze opdrachtoptie kan het gereedschap Compatibiliteit upgraden ook een map analyseren die verschillende modules bevat:

```bash
bin/uct upgrade:check /<dir>/<instance-name> -m /vendor/<vendor-name>/
```

Zie de [Het gereedschap uitvoeren in een opdrachtregelinterface](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/run.html) voor meer informatie over opdrachtregelinterface-opties.
