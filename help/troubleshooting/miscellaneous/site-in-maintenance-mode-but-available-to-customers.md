---
title: Site in onderhoudsmodus maar beschikbaar voor klanten
description: Dit artikel biedt een oplossing voor het moment waarop de onderhoudsmodus is ingeschakeld (een probleem met een Adobe Commerce-infrastructuur in de cloud), maar de winkel is nog steeds beschikbaar voor klanten.
exl-id: 61b81fbd-a382-44b5-94e9-5b6d72f11349
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Site in onderhoudsmodus maar beschikbaar voor klanten

Dit artikel biedt een oplossing voor het moment waarop de onderhoudsmodus is ingeschakeld (een probleem met een Adobe Commerce-infrastructuur in de cloud), maar de winkel is nog steeds beschikbaar voor klanten.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur (alle versies)

## Probleem

<u> Stappen om te reproduceren:</u>

1. Schakel de onderhoudsmodus voor de site in.
1. Ga naar de storefront.

<u> Verwacht resultaat:</u>

De onderhoudspagina wordt weergegeven.

<u> Ware resultaat:</u>

De winkelpagina&#39;s worden op de gebruikelijke wijze weergegeven.

## Oorzaak

Pagina&#39;s worden nog steeds in het cachegeheugen opgeslagen, zodat de onderhoudspagina niet wordt weergegeven.

## Oplossing voor de locatie is zichtbaar ondanks de onderhoudsmodus

1. SSH voor uw omgeving.
1. Voer de opdracht `php bin/magento cache:clean` uit.

## Gerelateerde lezing

[ laat of maak onderhoudswijze ](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-maint.html) in onze ontwikkelaarsdocumentatie toe onbruikbaar.
