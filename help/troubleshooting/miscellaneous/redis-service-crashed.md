---
title: Redis-service vastgelopen
description: In het artikel wordt aanbevolen hoe Redis moet worden hersteld.
exl-id: 5eb8fb70-0f41-433a-8d3f-c368781a2d1d
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# Redis-service vastgelopen

In het artikel wordt aanbevolen hoe Redis moet worden hersteld.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur 2.2.x, 2.3.x
* Adobe Commerce op locatie 2.2.x, 2.3x
* Alle versies van Redis

## Probleem

Traagheid of uitval van de website als gevolg van geheugenoverloop in Redis.

## Oorzaak

Geheugenoverloop kan ertoe leiden dat de service Redis vastloopt. Tijdens piektijd, kan de dienst Redis meer geheugen vereisen dan wat momenteel wordt toegewezen.

## Oplossing

Om huidige configuratie en gebruikt geheugen te controleren, stel het volgende bevel in CLI in werking. Het controleert op gebruikt geheugen, maxmemory, geëlimineerde sleutels, en Redis omhoog tijd in dagen:

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

De *REDIS\_PORT* en *REDIS\_HOST* variabelen kunnen worden opgehaald uit `app/etc/env.php`.

Als uit de uitvoer van de bovenstaande query blijkt dat het percentage vrij geheugen minder dan 40% is, [een ticket verzenden naar Adobe Commerce-ondersteuning](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) verzoeken om een verhoging van de `maxmemory` instellen in Redis Server. Als de waarde van de verwijderde toetsen niet &quot;0&quot; is of als de retoucheertijd in dagen gelijk is aan 0 (wat aangeeft dat Redis vandaag is vastgelopen), moet u ook [een ticket verzenden naar Adobe Commerce-ondersteuning](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) een onderzoek en een oplossing voor dit probleem aan te vragen.

## Verwante lezing

Meer informatie over Redis-geheugen vindt u in [Geheugenoptimalisatie opnieuw instellen](https://redis.io/topics/memory-optimization).
