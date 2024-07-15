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

* [ het Hulpmiddel van de Verenigbaarheid van de Verbetering ](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html) is compatibel met de versies van Adobe Commerce vanaf 2.3.0.

## Fout in segmentfout

<u> Oorzaak </u>:

Wanneer twee modules de zelfde naam hebben, toont het Hulpmiddel van de Verenigbaarheid van de Verbetering een fout van de segmenteringsfout.

<u> Oplossing </u>:

Om deze fout te vermijden, wordt aanbevolen het pad naar de module als argument op te geven:

```bash
bin/uct upgrade:check --current-version=2.4.4 path/to/the/module
```

>[!WARNING]
>
> Het gereedschap Compatibiliteit bijwerken kan de codebase mogelijk niet analyseren als deze cyclische afhankelijkheid tussen methoden bevat.

## Lege uitvoer

<u> Stappen om </u> te reproduceren:

1. Indien na het uitvoeren van deze opdracht:

   ```bash
   bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
   ```

1. De enige uitvoer is `Upgrade compatibility tool` :

   ```terminal
   bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
   Upgrade compatibility tool
   ```

<u> Oorzaak </u>:

De waarschijnlijke oorzaak is een PHP geheugenbeperking.

Er zijn twee mogelijke oplossingen om deze PHP geheugenbeperking te voorkomen.

<u> Oplossing 1 </u>:

Hef de geheugenbeperking op door `memory_limit` in te stellen op `-1` :

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

>[!NOTE]
>
> `M2_VERSION` is de Adobe Commerce-doelversie die u wilt vergelijken met uw Adobe Commerce-instantie.

<u> Oplossing 2 </u>:

Als u de optie `-m` toevoegt, kan het gereedschap Compatibiliteit upgraden elke specifieke module afzonderlijk analyseren om te voorkomen dat er twee modules met dezelfde naam in uw Adobe Commerce-instantie komen.

Met deze opdrachtoptie kan het gereedschap Compatibiliteit upgraden ook een map analyseren die verschillende modules bevat:

```bash
bin/uct upgrade:check /<dir>/<instance-name> -m /vendor/<vendor-name>/
```

Zie [ in werking stellen het hulpmiddel in een bevel-lijn interface ](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/run.html) pagina voor meer informatie over bevel-lijn interfaceopties.
