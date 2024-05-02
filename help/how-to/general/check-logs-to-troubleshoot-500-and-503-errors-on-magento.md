---
title: Logboeken controleren om 500- en 503-fouten op Adobe Commerce op te lossen
description: Dit artikel verklaart hoe te om ` access.log ` en verwante logboeken te controleren om 503 en 500 fouten problemen op te lossen, die door verkeer of ontoereikende servermiddelen kunnen worden veroorzaakt. Door het bestand "access.log" en de bijbehorende logboeken te bekijken, kunt u informatie vinden over wat problemen met Adobe Commerce kan veroorzaken op het gebied van cloudinfrastructuur.
exl-id: 47d7de6b-3e12-4e79-a5c1-c27a9196b99c
feature: Cloud, Logs
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# Logboeken controleren om 500- en 503-fouten op Adobe Commerce op te lossen

In dit artikel wordt uitgelegd hoe u de `access.log` en verwante logboeken om 503 en 500 fouten problemen op te lossen, die door verkeer of ontoereikende servermiddelen kunnen worden veroorzaakt. De `access.log` en verwante logbestanden kunnen informatie bevatten over wat problemen met Adobe Commerce kan veroorzaken op het gebied van cloudinfrastructuur.

<!--
Bob - not in TOC
-->

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, alle [ondersteunde versies](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html).

Als u logboeken voor deze serverfouten wilt weergeven, controleert u de `access.log` op de webserver, bijvoorbeeld `<ip address>` `<timestamp>` `<request uri>` `<response code>` `<referer url>`

Verwante logbestanden controleren:

1. Voer het volgende bevel in CLI uit als het op de huidige dag (voor Adobe Commerce op de architectuur van het de planplan van de wolkeninfrastructuur Pro) is. Of tot een bepaald punt in het verleden (voor Adobe Commerce op de architectuur van het Plan van de Aanzet van de wolkeninfrastructuur), aangezien de duur van de logboekdekking beperkt is, en logboekomwenteling niet beschikbaar is: `grep -r "\" [50[0-9]" /path/to/access.log` Als de fout in het verleden is voorgekomen stel het volgende bevel in CLI (Pro architectuur slechts): `zgrep "\" 50[0-9]" /path/to/access.log.<rotation ID>.gz`
1. Controleer vervolgens de `exception.log` en `error.log` of gelijkwaardig [geroteerd logbestand](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#log-rotation) (logs die automatisch worden geroteerd en gecomprimeerd wanneer ze een bepaalde bestandsgrootte bereiken) voor dezelfde tijdstempel om de mogelijke fout te zoeken en te zien wat er mogelijk is gebeurd om deze te hebben veroorzaakt. Opmerking: de `exception.log` en `error.log` stel de bovengenoemde bevelen in CLI in werking maar vervang `access.log` with `exception.log` of `error.log`.

## Gerelateerde lezing

* Zie [Logbestanden weergeven en beheren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) in de *Adobe Commerce on Cloud Infrastructure Guide*.
* Zie [Problemen met 503 fouten oplossen](/help/troubleshooting/miscellaneous/troubleshooting-503-errors.md) in onze kennisbasis voor ondersteuning.
* Zie [Troubleshooter voor het oplossen van problemen met de site Magento](/help/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.md) in onze kennisbasis voor ondersteuning.
