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

a. JA - Ga door naar [Stap 2](#step2)</a>.

b) NO - Terugkeer naar [support.magento.com](https://support.magento.com/hc/en-us) en zoek naar relevante artikelen voor probleemoplossing.

+++

## Stap 2 - Bevestig geïnstalleerde Redis-patches {#step-2}

+++Huidige Redis-patches geïnstalleerd?

a. JA - Ga door naar [Stap 3](#step3)</a>.

b. NO - Controleer of u de meest recente versie van het pakket hebt `magento-cloud-patches` geïnstalleerd. Dit pakket bevat de benodigde patches voor Redis. Ga naar [GitHub magneto-cloud-patches](https://github.com/magento/magento-cloud-patches/).

+++

## Stap 3 - Bevestigen van versie Redis wordt ondersteund {#step-3}

+++On Redis versies 3.2 of 5.0?

Controle door de volgende bevelen in CLI in werking te stellen. Pro of Staging: `$ redis-cli -p %port-number% info | grep redis_version`, waarbij `%port-number%` is het nummer van de poort die u kunt vinden in het `app/etc/env.php` of door een van de volgende opdrachten uit te voeren: `$ vendor/bin/ece-tools env:config:show | grep -i redis -A 3` of `$ cat app/etc/env.php | grep redis -A 3` Starter of integratie: `$ redis-cli -h 'redis.internal' info | grep redis_version`

a. JA - Ga door naar [Stap 4](#step4).

b. NO - Adobe Commerce ondersteunt Redis versies 3.2 en 5.0. Als u Adobe Commerce uitvoert op cloudinfrastructuur 2.3.3 of hoger, raden we u aan een upgrade naar Redis 5 uit te voeren. Raadpleeg voor installatie-stappen op Adobe Commerce over de architectuur van de cloudinfrastructuur, integratie en starteromgevingen in de cloud, de [Adobe Commerce on cloud Infrastructure > Redis-service instellen](https://devdocs.magento.com/cloud/project/services-redis.html)</a> in onze ontwikkelaarsdocumentatie. **U moet [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om de de dienstconfiguratie op Pro architectuur te veranderen Productie en het Opvoeren milieu&#39;s. Voor Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.5+ wordt bovendien een uitgebreide Redis-cacheimplementatie aanbevolen. Dit type van Redis geheim voorgeheugenimplementatie verstrekt verhogingen die het aantal vragen aan Redis minimaliseren die op elk Adobe Commerce verzoek worden uitgevoerd. Raadpleeg voor stappen [Uitgebreide Redis cache-implementatie Adobe Commerce 2.3.5+](https://support.magento.com/hc/en-us/articles/360049292532) in onze kennisbasis voor ondersteuning. Voor alle andere Adobe Commerce-gebruikers raadpleegt u [Adobe Commerce Configuration Guide > Configure Redis](https://devdocs.magento.com/guides/v2.4/config-guide/redis/config-redis.html) in onze ontwikkelaarsdocumentatie, voor stappen.

+++

## Stap 4 - verifieer recentste versie van ECE-Hulpmiddelen {#step-4}

+++Hebt u de nieuwste versie van [ECE Tools > v2002.1.1](https://github.com/magento/ece-tools/releases)?

Controleer welke versie u door het bevel in CLI/Terminal in werking te stellen hebt: `$php vendor/bin/composer info magento/ece-tools`.

a. JA - Ga door naar [Stap 5](#step5).

b) NO - [ECE-gereedschappen upgraden](https://devdocs.magento.com/cloud/project/ece-tools-update.html) in de meest recente versie.

+++

## Stap 5 - bepaal netwerkverkeer {#step-5}

+++Is er veel netwerkverkeer tussen app en Redis?

a. JA - probeer het volgende: zorg voor een niet-gesplitste architectuur [secundaire verbinding](/help/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.md) wordt gebruikt. Voor gesplitste architectuur [L2-cache moet zijn ingeschakeld](https://devdocs.magento.com/guides/v2.4/config-guide/cache/two-level-cache.html).

b. NO - Configuratie van L2-cache configureren door [Herdis Backend bijwerken](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend). Doorgaan naar [Stap 6](#step6).

+++

## Stap 6 - De snelheid van de site controleren {#step-6}

+++Werkt de site nog steeds langzaam, nadat de L2-cache is ingeschakeld?

a. JA - Controleer de tijdelijke map `/dev/shm` om te zien of moet u ruimte verhogen. Als u meer ruimte nodig hebt [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
b. NO - Het inschakelen van L2-cache lijkt uw problemen met Redis op te lossen.

+++

[Terug naar stap 1](#step-1)
