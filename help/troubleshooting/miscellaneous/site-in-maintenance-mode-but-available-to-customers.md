---
title: Site in onderhoudsmodus maar beschikbaar voor klanten
description: Dit artikel biedt een oplossing voor het moment waarop de onderhoudsmodus is ingeschakeld (een probleem met een Adobe Commerce-infrastructuur in de cloud), maar de winkel is nog steeds beschikbaar voor klanten.
exl-id: 61b81fbd-a382-44b5-94e9-5b6d72f11349
feature: Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

[&#x200B; laat of maak onderhoudswijze &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in onze ontwikkelaarsdocumentatie toe onbruikbaar.
