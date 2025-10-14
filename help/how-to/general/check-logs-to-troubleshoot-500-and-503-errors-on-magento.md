---
title: Logboeken controleren om 500- en 503-fouten op Adobe Commerce op te lossen
description: Dit artikel verklaart hoe te om &grave; access.log &grave; en verwante logboeken te controleren om 503 en 500 fouten problemen op te lossen, die door verkeer of ontoereikende servermiddelen kunnen worden veroorzaakt. Door het bestand "access.log" en de bijbehorende logboeken te bekijken, kunt u informatie vinden over wat problemen met Adobe Commerce kan veroorzaken op het gebied van cloudinfrastructuur.
exl-id: 47d7de6b-3e12-4e79-a5c1-c27a9196b99c
feature: Cloud, Logs
source-git-commit: 66ac9de94e9a4a1eccdb5aac1875ecf0a0637e90
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Logboeken controleren om 500- en 503-fouten op Adobe Commerce op te lossen

In dit artikel wordt uitgelegd hoe u de `access.log` en verwante logboeken kunt controleren om 503- en 500-fouten op te lossen. Dit kan worden veroorzaakt door verkeer of onvoldoende serverbronnen. Als u de `access.log` - en verwante logbestanden bekijkt, kunt u informatie weergeven over wat problemen met Adobe Commerce kan veroorzaken in de cloud-infrastructuur.

<!--
Bob - not in TOC
-->

## Betrokken producten en versies

* Adobe Commerce op wolkeninfrastructuur, alle [&#x200B; gesteunde versies &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html?lang=nl-NL).

Als u logboeken voor deze serverfouten wilt weergeven, controleert u de `access.log` op de webserver, bijvoorbeeld `<ip address>` `<timestamp>` `<request uri>` `<response code>` `<referer url>`

Verwante logbestanden controleren:

1. Voer het volgende bevel in CLI uit als het op de huidige dag (voor Adobe Commerce op de architectuur van het de planplan van de wolkeninfrastructuur Pro) is. Of tot een bepaald punt in het verleden (voor Adobe Commerce op de architectuur van het Plan van de Aanzet van de wolkeninfrastructuur), aangezien de duur van de logboekdekking beperkt is, en logboekomwenteling niet beschikbaar is: `grep -r "\" [50[0-9]" /path/to/access.log` als de fout in het verleden is voorgekomen stel het volgende bevel in CLI (Pro architectuur slechts): `zgrep "\" 50[0-9]" /path/to/access.log.<rotation ID>.gz`
1. Dan controleer `exception.log` en `error.log` of het gelijkwaardige [&#x200B; geroteerde logboek &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html?lang=nl-NL#log-rotation) (logboeken die automatisch worden geroteerd en worden samengeperst wanneer zij een bepaalde dossiergrootte) voor zelfde timestamp bereiken om van de potentiële fout de plaats te bepalen en te zien wat zou kunnen voorkomen om het te veroorzaken. Opmerking: als u de opdrachten `exception.log` en `error.log` hierboven in de CLI wilt controleren, maar `access.log` wilt vervangen door `exception.log` of `error.log` .

## Gerelateerde lezing

* Zie [&#x200B; Logboeken van de Mening en beheer &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=nl-NL) in *Adobe Commerce op de Gids van de Infrastructuur van de Wolk*.
* Zie [&#x200B; het Oplossen van problemen 503 fouten &#x200B;](/help/troubleshooting/miscellaneous/troubleshooting-503-errors.md) in onze basis van de steunkennis.