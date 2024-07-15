---
title: Redis troubleshooter op Adobe Commerce
description: Dit artikel is een hulpprogramma voor het oplossen van problemen voor Adobe Commerce op locatie en Adobe Commerce voor bedrijven met cloudinfrastructuur die problemen hebben met Redis. Klik op elke vraag om het antwoord in elke stap van de probleemoplosser te onthullen. Afhankelijk van uw symptomen en configuratie, zal de probleemoplosser verklaren hoe te om versie en geheugenkwesties problemen op te lossen en prestaties te optimaliseren.
exl-id: 241abcfd-33b8-449b-b385-32950bd26320
feature: Services, Support
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 0%

---

# Redis troubleshooter op Adobe Commerce

Dit artikel is een hulpprogramma voor het oplossen van problemen voor Adobe Commerce op locatie en Adobe Commerce voor bedrijven met cloudinfrastructuur die problemen hebben met Redis. Klik op elke vraag om het antwoord in elke stap van de probleemoplosser te onthullen. Afhankelijk van uw symptomen, zal de probleemoplosser verklaren hoe u versie en geheugenkwesties kunt problemen oplossen, en prestaties optimaliseren.

## Stap 1 - Probleem met opnieuw verzenden {#step-1}

+++Probleem opnieuw verzenden?

a. JA - ga aan [ Stap 2 ](#step2)</a> te werk.

b. NO - Terugkeer aan [ support.magento.com ](https://support.magento.com/hc/en-us) en onderzoek naar relevante het oplossen van problemenartikelen.

+++

## Stap 2 - Bevestig geïnstalleerde Redis-patches {#step-2}

+++Huidige Redis-patches geïnstalleerd?

a. JA - ga aan [ Stap 3 ](#step3)</a> te werk.

b. NO - Controleer of de laatste versie van het pakket `magento-cloud-patches` is geïnstalleerd. Dit pakket bevat de benodigde patches voor Redis. Om tot [ toegang te hebben gaat GitHub magneto-cloud-flarden ](https://github.com/magento/magento-cloud-patches/).

+++

## Stap 3 - Bevestigen van versie Redis wordt ondersteund {#step-3}

+++On Redis versies 3.2 of 5.0?

Controle door de volgende bevelen in CLI in werking te stellen. Pro of Staging: `$ redis-cli -p %port-number% info | grep redis_version` , waarbij `%port-number%` het nummer van de poort is, die u vindt in het `app/etc/env.php` -bestand of door een van de volgende opdrachten uit te voeren: `$ vendor/bin/ece-tools env:config:show | grep -i redis -A 3` of `$ cat app/etc/env.php | grep redis -A 3` Starter of Integration: `$ redis-cli -h 'redis.internal' info | grep redis_version`

a. JA - ga aan [ Stap 4 ](#step4) te werk.

b. NO - Adobe Commerce ondersteunt Redis versies 3.2 en 5.0. Als u Adobe Commerce uitvoert op cloudinfrastructuur 2.3.3 of hoger, raden we u aan een upgrade naar Redis 5 uit te voeren. Voor opstellingsstappen op Adobe Commerce op de architectuur van het plan van de wolkeninfrastructuur Pro, Integratie en Startermilieu&#39;s met inbegrip van de hoofdtak, verwijs naar [ Adobe Commerce op wolkeninfrastructuur > de dienst van Redis van de Opstelling ](https://devdocs.magento.com/cloud/project/services-redis.html) </a> in onze ontwikkelaarsdocumentatie. **U moet [ een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voorleggen om de de dienstconfiguratie op Pro architectuurProductie en het Opvoeren milieu&#39;s te veranderen. Voor Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.5+ wordt bovendien een uitgebreide Redis-cacheimplementatie aanbevolen. Dit type van Redis geheim voorgeheugenimplementatie verstrekt verhogingen die het aantal vragen aan Redis minimaliseren die op elk Adobe Commerce verzoek worden uitgevoerd. Voor stappen, verwijs naar [ Uitgebreide Redis geheim voorgeheugenimplementatie Adobe Commerce 2.3.5+ ](https://support.magento.com/hc/en-us/articles/360049292532) in onze basis van de steunkennis. Voor alle andere gebruikers van Adobe Commerce, verwijs naar [ de Gids van de Configuratie van Adobe Commerce > vormt Redis ](https://devdocs.magento.com/guides/v2.4/config-guide/redis/config-redis.html) in onze ontwikkelaarsdocumentatie, voor stappen.

+++

## Stap 4 - verifieer recentste versie van ECE-Hulpmiddelen {#step-4}

+++hebt u de recentste versie van [ ECE Hulpmiddelen > v2002.1.1 ](https://github.com/magento/ece-tools/releases)?

Controleer welke versie u hebt door het bevel in CLI/Terminal in werking te stellen: `$php vendor/bin/composer info magento/ece-tools`.

a. JA - ga aan [ Stap 5 ](#step5) te werk.

b. NO - [ Verbetering ECE-Hulpmiddelen ](https://devdocs.magento.com/cloud/project/ece-tools-update.html) aan de recentste versie.

+++

## Stap 5 - bepaal netwerkverkeer {#step-5}

+++Is er veel netwerkverkeer tussen app en Redis?

a. JA - probeer het volgende: Voor een niet-gesplitste architectuur, zorg a [ secundaire verbinding ](/help/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.md) wordt gebruikt. Voor gespleten architectuur, moet het [ L2 geheime voorgeheugen ](https://devdocs.magento.com/guides/v2.4/config-guide/cache/two-level-cache.html) worden toegelaten.

b. NO - vorm L2 geheim voorgeheugenconfiguratie door [ Bijgewerkt Redis Backend ](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend). Ga aan [ Stap 6 ](#step6) te werk.

+++

## Stap 6 - De snelheid van de site controleren {#step-6}

+++Werkt de site nog steeds langzaam, nadat de L2-cache is ingeschakeld?

a. JA - Controleer de tijdelijke map `/dev/shm` om te zien of u meer ruimte nodig hebt. Als u meer ruimte nodig hebt, [ voorlegt een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
b. NO - Het inschakelen van L2-cache lijkt uw problemen met Redis op te lossen.

+++

[Terug naar stap 1](#step-1)
