---
title: Hoe te om een "scrubbed"stortplaats te creëren wanneer gevraagd door steunagent
description: Dit artikel biedt informatie over hoe u een 'scrubbed'-stortplaats (back-up) van uw database en code kunt maken vanuit de Adobe Commerce Admin wanneer u daarom wordt gevraagd om er een te leveren door een Adobe Commerce-ondersteuningsagent. Deze dump sluit uw mediabestanden uit om het proces te versnellen en een veel kleiner bestand te maken. Alle gevoelige gegevens worden gehashed wanneer het maken van de gegevensbestandsteun.
exl-id: ad088bd2-3f92-416e-89f0-d037d53cd6a9
source-git-commit: e07ade849a4105b5e499b5282d75cb1b5321b6ea
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# Hoe te om een &quot;scrubbed&quot;stortplaats te creëren wanneer gevraagd door steunagent


## Betrokken producten en versies

Adobe Commerce (alle implementatiemethoden) 2.3.x, 2.4.x.

## Een &#39;scrubbed&#39;-stortplaats maken

Maak een &#39;scrubbed&#39;-dump van de beheerder:

1. In Commerce Admin, ga naar **Systeem** > **Steun** > **de Collector van Gegevens**.
1. Klik **Nieuwe Steun**.
1. Na een paar notulen, klik **verfrissen Status** (kan langer duren, herhaal om de 5 minuten tot voltooide).
1. Verplaats de gegenereerde dump-bestanden vanuit de map `/var/support` naar de hoofdmap van Adobe Commerce.

Vervolgens kunt u ondersteuning bieden voor de directe downloadkoppeling naar de dump-bestanden (uw winkeladres en de bestandsnaam zoals deze worden weergegeven).

Als u kwesties hebt die tot dumps van Admin leiden, denk na gebruikend bevelen CLI zoals die in [ worden beschreven in werking stellen de steunnut ](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-spt-util.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

* [ creeer volledige gegevensbestandsteun voor Adobe Commerce op wolkeninfrastructuur ](/help/how-to/general/create-database-dump-on-cloud.md) in onze basis van steunkennis.
