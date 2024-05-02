---
title: Nieuwe klanten die na CSV-import niet worden weergegeven in het klantenraster
description: Dit artikel biedt een oplossing voor het probleem wanneer u geen nieuwe klanten ziet onder **Customers** gt; **All customer*** after an import from a `.csv` file. De oplossing moet de ` customer_grid' indexer aan "Update op sparen"wijze plaatsen en manueel het klantennet opnieuw indexeren.
exl-id: e4d9d60a-a0d1-4602-924e-a338e56de61d
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Nieuwe klanten die na CSV-import niet worden weergegeven in het klantenraster

Dit artikel biedt een oplossing voor het probleem wanneer u geen nieuwe klanten onder **Klanten** > **Alle klanten** na invoer uit een `.csv` bestand. De oplossing is het instellen van de `customer_grid` indexeer aan &quot;Update op sparen&quot;wijze en herdex manueel het klantennet.

## Betrokken versies

* Adobe Commerce op locatie 2.2.0 en hoger
* Adobe Commerce over cloudinfrastructuur 2.2.0 en hoger

## Probleem

Na het invoeren van nieuwe klanten uit een `.csv` bestand met de native Adobe Commerce-importfunctionaliteit, kan het zijn dat je de nieuwe klantrecords niet kunt bekijken onder **Klanten** > **Alle klanten** in de Admin totdat u de `customer_grid` indexeerprogramma.

## Oorzaak

De indexeringsmodus &quot;Update on Schedule&quot; in Adobe Commerce 2.2.0 en hoger biedt geen ondersteuning voor de `customer_grid` indexeerprogramma vanwege prestatieproblemen.

## Oplossing

Vorm `customer_grid` indexeer die opnieuw moet worden gedexeerd met de modus &quot;Bijwerken op opslaan&quot;. Voer hiertoe de volgende stappen uit:

1. Meld u aan bij de Commerce-beheerder.
1. Klikken **Systeem** > **Gereedschappen** > **Indexbeheer**.
1. Schakel het selectievakje naast de indexeerfunctie voor klantenraster in.
1. In de **Handelingen** vervolgkeuzelijst, selecteert u *Bijwerken bij opslaan*.
1. Klikken **Verzenden**.

We raden u ook aan de `customer_grid` indexeer na het vormen van de indexerende wijze om ervoor te zorgen dat de index bijgewerkt is en met kroon kan werken. Gebruik de volgende opdracht om opnieuw te indexeren:

`bin/magento indexer:reindex customer_grid`

## Meer informatie

Koppelingen naar verwante onderwerpen in onze documentatie voor ontwikkelaars:

* [Overzicht van indexering](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html)
* [De indexen beheren](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html)
