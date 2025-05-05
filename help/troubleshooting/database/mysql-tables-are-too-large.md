---
title: '[!DNL MySQL] tabellen zijn te groot'
description: Dit artikel bespreekt waarom het een kwestie is wanneer om het even welke  [!DNL MySQL]  lijst groter wordt dan 1 GB en hoe te om dit te verhinderen.
exl-id: 43f74e3b-7f2e-428c-9964-56d2ce98a34d
feature: Services
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# [!DNL MySQL] tabellen zijn te groot

In dit artikel wordt besproken waarom het een probleem is wanneer een [!DNL MySQL] -tabel groter wordt dan 1 GB en hoe u dit kunt voorkomen.

## Betrokken producten en versies:

* Adobe Commerce op cloudinfrastructuur 2.x.x
* Adobe Commerce op locatie 2.x.x

## Probleem

De grootte van [!DNL MySQL] -tabellen heeft niet rechtstreeks invloed op de prestaties van de site. Als een tabel echter groot is, betekent dit dat er vaak invoegbewerkingen in deze tabel plaatsvinden, met mogelijk extra gegevens of verouderde gegevens. [!DNL MySQL] is ontworpen voor databases, waarbij de verhouding tussen lees- en schrijfbewerkingen 80%/20% is.  Voor de grote tabellen, 1 GB en meer, [!DNL MySQL] indexen, die worden ontworpen om prestaties bij gelezen verrichtingen te versnellen, zouden prestaties bij schrijven verrichtingen kunnen degraderen.

## Oplossing

Houd rekening met de volgende opties om een afname van de prestaties te voorkomen:

* Maak een CRON-taak, die grote tabellen opschoont. Zie [ grote  [!DNL MySQL]  lijsten ](/help/how-to/general/find-large-mysql-tables.md) vinden in onze basis van steunkennis voor aanbevelingen op hoe te om grote lijsten te identificeren.
* Gebruik voor tabellen die groter zijn dan 1 GB een [!DNL MySQL] -engine die is geoptimaliseerd voor het schrijven van logbestanden. Bijvoorbeeld de Archiefengine.
* Werk de functionaliteit bij om te voorkomen dat logbestanden in de database worden opgeslagen.

## Gerelateerde lezing

* [ de Overmaatse lijsten van het veranderingslogboek die vertragingen in entiteiten updates ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/database/changes-in-the-database-are-not-reflected-on-the-storefront) in onze basis van de steunkennis veroorzaken
* [ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/nl/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
