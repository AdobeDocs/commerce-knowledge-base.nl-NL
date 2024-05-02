---
title: Uploaden database verliest verbinding met MySQL
description: Dit artikel biedt een oplossing voor het moment dat de databaseupload de verbinding met MySQL verliest.
exl-id: 6051cea1-8292-4a81-8908-eb516cb4a32b
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Uploaden database verliest verbinding met MySQL

Dit artikel biedt een oplossing voor het moment dat de databaseupload de verbinding met MySQL verliest.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur 2.2.x, 2.3.x

## Probleem

De database wordt niet geüpload naar primaire/integratievestigingen op Adobe Commerce op de architectuur van het Pro-abonnement voor cloudinfrastructuur van de cloudinfrastructuur of naar een filiaal op Adobe Commerce op de Starter-planarchitectuur van de cloudinfrastructuur, met als symptoom dat er geen verbinding kan worden gemaakt. U ziet deze fout in CLI.

```
web@ddc35c264bd89a72042f1f3e5a:~$ mysql -h database.internal -u user -p main
Enter password:
ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"
```

## Oorzaak

Dit komt meestal door een gebrek aan schijfruimte voor het importeren van de database.

## Oplossing

Controleer of er onvoldoende schijfruimte is. Voer hiertoe de `netcat` bevel in CLI tegen gegevensbestandhaven 3306; er zal een schijf volledig bericht zijn als het volledig is:

```
web@ddc35c264bd89a72042f1f3e5a:~$ nc database.internal 3306
Database out of space
```

U moet meer ruimte toewijzen aan de database in uw `services.yaml` en implementeren als u wat ruimte ongebruikt hebt. Zie voor stappen [Serviceschijfruimte](https://devdocs.magento.com/cloud/project/manage-disk-space.html#service-disk-space).

Nota: Op het Pro architectuurplan, kunt u de toegewezen ruimte op uw verdeling controleren door het volgende bevel in werking te stellen: `df -h`

Verwacht uitvoer vergelijkbaar met de volgende uitvoer. In dit voorbeeld wordt 10 GB van de toegewezen 25 GB gebruikt, waarbij 15 GB van MySQL-ruimte niet wordt gebruikt.

```
f240jestone3wt@i-087r2a25fdac80726:~$ df -h|grep 'File\|xvd'
Filesystem                                         Size  Used Avail Use% Mounted on
/dev/xvda1                                          59G   15G   42G  26% /
/dev/xvdj                                           25G   10G   15G  41% /data/mysql
/dev/xvdi                                           25G   22G  2.6G  90% /data/exports
```

## Gerelateerde lezing

[Schijfruimte beheren](https://devdocs.magento.com/cloud/project/manage-disk-space.html) in onze documentatie voor ontwikkelaars
