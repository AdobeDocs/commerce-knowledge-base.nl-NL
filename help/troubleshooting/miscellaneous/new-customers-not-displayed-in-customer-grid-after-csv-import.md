---
title: Nieuwe klanten die na CSV-import niet worden weergegeven in het klantenraster
description: Dit artikel bevat een oplossing voor het probleem wanneer u geen nieuwe klanten ziet onder **Klanten**** amp;gt; **Alle klanten*** na het importeren uit een `.csv`-bestand. De oplossing moet de ` customer_grid' indexer aan "Update op sparen"wijze plaatsen en manueel het klantennet opnieuw indexeren.
exl-id: e4d9d60a-a0d1-4602-924e-a338e56de61d
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Nieuwe klanten die na CSV-import niet worden weergegeven in het klantenraster

Dit artikel verstrekt een moeilijke situatie voor de kwestie wanneer u geen nieuwe klanten onder **Klanten** kunt zien > **Alle klanten** na de invoer van a `.csv` dossier. De oplossing is om de `customer_grid` indexer in te stellen op de modus &quot;Bijwerken bij opslaan&quot; en het klantenraster handmatig opnieuw te indexeren.

## Betrokken versies

* Adobe Commerce op locatie 2.2.0 en hoger
* Adobe Commerce over cloudinfrastructuur 2.2.0 en hoger

## Probleem

Na het invoeren van nieuwe klanten van een `.csv` dossier gebruikend de inheemse de invoerfunctionaliteit van Adobe Commerce, zou u de nieuwe klantenverslagen onder **Klanten** kunnen niet zien > **Alle klanten** in Admin tot u manueel de `customer_grid` indexeerder opnieuw indexeert.

## Oorzaak

De indexeringsmodus &quot;Update on Schedule&quot; in Adobe Commerce 2.2.0 en hoger biedt vanwege prestatieproblemen geen ondersteuning voor de indexeerfunctie van `customer_grid` .

## Oplossing

Configureer de `customer_grid` -indexeerfunctie die opnieuw moet worden ingesteld met de modus &quot;Bijwerken bij opslaan&quot;. Voer hiertoe de volgende stappen uit:

1. Meld u aan bij de Commerce-beheerder.
1. Klik **Systeem** > **>** het Beheer van de Index **.**
1. Schakel het selectievakje naast de indexeerfunctie voor klantenraster in.
1. In de **drop-down lijst van Acties**, uitgezochte *Update op sparen*.
1. Klik **voorleggen**.

We raden u ook aan de indexeerfunctie van `customer_grid` handmatig opnieuw te indexeren nadat u de indexmodus hebt geconfigureerd om ervoor te zorgen dat de index up-to-date is en met uitsnijden kan werken. Gebruik de volgende opdracht om opnieuw te indexeren:

`bin/magento indexer:reindex customer_grid`

## Meer informatie

Koppelingen naar verwante onderwerpen in onze documentatie voor ontwikkelaars:

* [ Indexerend overzicht ](https://developer.adobe.com/commerce/php/development/components/indexing/)
* [ beheer de indexen ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers)
