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

1. Ga in Commerce Admin naar **Systeem** > **Ondersteuning** > **Gegevensverzameling**.
1. Klikken **Nieuwe back-up**.
1. Na een paar minuten klikt u op **Status vernieuwen** (kan langer duren, herhaal deze elke 5 minuten tot het voltooien).
1. Plaats de gegenereerde stortplaatsbestanden opnieuw vanuit de `/var/support` naar de hoofdmap van Adobe Commerce.

Vervolgens kunt u ondersteuning bieden voor de directe downloadkoppeling naar de dump-bestanden (uw winkeladres en de bestandsnaam zoals deze worden weergegeven).

Als u problemen ondervindt bij het maken van dumps vanuit de beheerder, kunt u overwegen CLI-opdrachten te gebruiken, zoals beschreven in [Voer de hulpprogramma&#39;s voor ondersteuning uit](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-spt-util.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

* [Volledige databaseback-up voor Adobe Commerce maken op cloudinfrastructuur](/help/how-to/general/create-database-dump-on-cloud.md) in onze kennisbasis voor ondersteuning.
