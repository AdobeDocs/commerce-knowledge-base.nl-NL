---
title: MySQL-tabellen zijn te groot
description: In dit artikel wordt besproken waarom dit een probleem is wanneer een MySQL-tabel groter wordt dan 1 GB en hoe u dit kunt voorkomen.
exl-id: 43f74e3b-7f2e-428c-9964-56d2ce98a34d
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# MySQL-tabellen zijn te groot

In dit artikel wordt besproken waarom dit een probleem is wanneer een MySQL-tabel groter wordt dan 1 GB en hoe u dit kunt voorkomen.

## Betrokken producten en versies:

* Adobe Commerce op cloudinfrastructuur 2.x.x
* Adobe Commerce op locatie 2.x.x

## Probleem

De grootte van MySQL-tabellen heeft niet rechtstreeks invloed op de prestaties van de site. Als een tabel echter groot is, betekent dit dat er vaak invoegbewerkingen in deze tabel plaatsvinden, met mogelijk extra gegevens of verouderde gegevens. MySQL is ontworpen voor databases, waarbij de verhouding tussen lees- en schrijfbewerkingen 80%/20% is.  Voor de grote lijsten, 1 GB en meer, zouden de indexen MySQL, die worden ontworpen om prestaties bij gelezen verrichtingen te versnellen, prestaties bij schrijven verrichtingen kunnen degraderen.

## Oplossing

Houd rekening met de volgende opties om een afname van de prestaties te voorkomen:

* Maak een CRON-taak, die grote tabellen opschoont. Zie [ grote lijsten MySQL ](/help/how-to/general/find-large-mysql-tables.md) in onze basis van steunkennis voor aanbevelingen vinden op hoe te om grote lijsten te identificeren.
* Gebruik voor tabellen die groter zijn dan 1 GB een MySQL-engine die is geoptimaliseerd voor het schrijven van logbestanden. Bijvoorbeeld de Archiefengine.
* Werk de functionaliteit bij om te voorkomen dat logbestanden in de database worden opgeslagen.

## Gerelateerde lezing

[ Overmaatse lijsten van het veranderingslogboek die vertragingen in entiteiten veroorzaken werkt ](/help/troubleshooting/database/changes-in-the-database-are-not-reflected-on-the-storefront.md) in onze basis van de steunkennis bij.
