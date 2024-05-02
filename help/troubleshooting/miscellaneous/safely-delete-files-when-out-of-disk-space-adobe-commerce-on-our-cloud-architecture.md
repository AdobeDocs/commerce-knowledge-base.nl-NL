---
title: Bestanden veilig verwijderen wanneer onvoldoende ruimte beschikbaar is op schijf in Adobe Commerce op cloudinfrastructuur
description: Dit artikel biedt een oplossing voor het geval dat er onvoldoende schijfruimte is en bestanden veilig moeten worden verwijderd. Lees voordat u deze handeling overweegt [Schijfruimte beheren] (https://devdocs.magento.com/cloud/project/manage-disk-space.html#no-space-left) in de ontwikkelaarsdocumentatie. Controleer de stappen in dit artikel als de stappen in dat artikel niet geschikt zijn voor u of als u het probleem niet oplost.
exl-id: 6b0a5c1a-8db4-49d7-a785-b4e0bbaea0df
feature: Cloud, Paas
role: Developer
source-git-commit: 6af353bb379ee88248342a7cb514dd9d36d47a92
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# Bestanden veilig verwijderen wanneer onvoldoende ruimte beschikbaar is op schijf in Adobe Commerce op cloudinfrastructuur

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur: 2.3.0-2.3.7, 2.4.0-2.4.2-p1
* Dit geldt specifiek voor toegewijde Pro-clusters. Starter- en integratieomgevingen zijn één knooppunt en hebben geen `/data/exports` directory.

## Tekens van weinig schijfruimte

Tekens die u bijna geen schijfruimte meer hebt, kunnen vastlopen op implementatie, volledige schijfwaarschuwingen en slechte prestaties.
Om de hoeveelheid schijfruimte te zien die door het dossiersysteem wordt gebruikt stel het volgende bevel in CLI/Terminal in werking:

`df -h`


## Bestanden veilig verwijderen om schijfruimte te vergroten

U kunt bestanden van de koppelingspunten van de toepassing verwijderen vanuit uw `/app` pad of doorheen `/mnt/shared`. Dit zijn twee verschillende manieren om toegang te krijgen tot dezelfde bestanden.

>[!WARNING]
>
>**De inhoud van`/data/exports`**.
>
>`/data/exports` is de onderliggende opslag achter het gedeelde bestandssysteem en wordt beheerd door GlusterFS.
>
>Het bestandssysteem bevat niet alleen de bestandsinhoud, maar ook metagegevens over de status van het bestandssysteem, zodat synchronisatie >tussen de knooppunten van uw cluster mogelijk is. **Als u bestanden rechtstreeks in dit bestandssysteem wijzigt of verwijdert, wordt het gedeelde >bestandssysteem beschadigd. Hiervoor is uitgebreide reparatie of gegevensherstel vereist.**

Om van de grootste dossiers de plaats te bepalen die goede kandidaten voor het ontruimen zouden kunnen zijn, stel het volgende bevel in werking (op grote of bezige projecten kunnen tot een uur duren):

```bash
FS='/data/exports';NUMRESULTS=20;resize;clear; echo "Please find below the Largest Directories and Files:";date;df -h $FS; echo "Largest Directories:";nice -n 19 find /app/*/ -type d -ls 2>/dev/null| sort -rnk1| head -n $NUMRESULTS| awk '
{printf "%d MB %s\n", $1/1024,$2}
';echo "Largest Files:"; nice -n 19 find /app/*/ -type f -ls 2>/dev/null| sort -rnk7| head -n $NUMRESULTS|awk '
{printf "%d MB\t%s\n", ($7/1024)/1024,$NF}
'; echo "Please use the above information to clear any unwanted data from the server, it is important this is done as soon as possible to ensure your server stays functional.";
```

De uitvoer van de opdracht bevat een lijst met de grootste bestanden en mappen waarvan de grootte is opgegeven.

## Gerelateerde lezing

In onze kennisbasis voor ondersteuning:

* [Schijfruimte vergroten voor integratieomgeving op cloud](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md)
* [Weinig schijfruimte](/help/troubleshooting/miscellaneous/low-disk-space.md)

In onze documentatie voor ontwikkelaars:

* [Schijfruimte beheren](https://devdocs.magento.com/cloud/project/manage-disk-space.html)
