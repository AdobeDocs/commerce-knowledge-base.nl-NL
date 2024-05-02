---
title: Elasticsearch in Adobe Commerce probleemoplosser
description: Problemen met de Elasticsearch in Adobe Commerce kunnen worden opgelost met het hulpprogramma voor het oplossen van problemen met Elasticsearch. Klik op elke vraag om het antwoord in elke stap van de probleemoplosser te onthullen.
exl-id: acae0da0-2918-4021-9fbe-c138940c5a72
feature: Categories
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 0%

---

# Elasticsearch in Adobe Commerce probleemoplosser

Problemen met de Elasticsearch in Adobe Commerce kunnen worden opgelost met het hulpprogramma voor het oplossen van problemen met Elasticsearch. Klik op elke vraag om het antwoord in elke stap van de probleemoplosser te onthullen.

>[!WARNING]
>
>Op Adobe Commerce over cloudinfrastructuur dient u te weten dat serviceupgrades niet naar de productieomgeving kunnen worden doorgevoerd zonder dat ons infrastructuurteam hiervan 48 uur op de hoogte wordt gesteld. Dit is nodig omdat wij ervoor moeten zorgen dat wij een ingenieur van de infrastructuursteun beschikbaar hebben om uw configuratie binnen een gewenst tijdsbestek met minimale onderbreking aan uw productiemilieu bij te werken. Dus 48 uur voor het moment dat uw veranderingen in productie moeten zijn [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) het gedetailleerd van uw vereiste de dienstverbetering en het verklaren van de tijd wanneer u het verbeteringsproces wilt beginnen.

## Stap 1 - Controleren op probleem met Elasticsearch {#step-1}

+++**Zou uw probleem betrekking kunnen hebben op Elasticsearch?**

Problemen met de Elasticsearch die worden aangegeven door foutberichten. &quot;_Geen levende knopen die in uw cluster worden gevonden&quot;,_ ontbrekende producten en de weergave van oude productinformatie.

a. JA - Ga door naar [Stap 2](#step-2).\
b. NO - Zoek nogmaals op relevante zoektermen in de [Adobe Commerce Help Center Knowledge Base](https://support.magento.com/hc).

+++

## Stap 2 - Controleren op installatieprobleem {#step-2}

+++**Is het een nieuwe installatie van Elasticsearch?**

a. JA - [Controleer of de Elasticsearch correct is geïnstalleerd.](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) Controleer ook of u op Adobe Commerce werkt op cloudinfrastructuur 2.3.1 of hoger. Handelaren die een upgrade naar Adobe Commerce hebben uitgevoerd op een cloudinfrastructuur (versie 2.3.1 en hoger) en die een versie van Elasticsearch hebben die ouder is dan 6.x, kunnen fouten ondervinden bij de implementatie. Om deze kwestie op te lossen moeten de de cliëntmodule en dienst van de Elasticsearch van de Elasticsearch op de recentste geadviseerde versies zijn. Zie voor stappen [Problemen met Elasticsearch na Adobe Commerce op cloudinfrastructuur 2.3.1+-upgrade](/help/troubleshooting/elasticsearch/elasticsearch-issues-after-magento-commerce-cloud-2-3-1-upgrade.md).\
b. NO - Controleer de gezondheid van uw cluster. Als u zich op een Pro het opvoeren of productiemilieu bevindt stel dit bevel in werking: `curl -m1 localhost:9200/_cluster/health?pretty`. Als u op een integratiemilieu (dat alle takken van de Aanzet omvat) loopt `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty`. Doorgaan naar [Stap 3](#step-3).

+++

## Stap 3 - controleer of de cluster Elasticsearch beschikbaar is {#step-3}

+++**Hebt u een servicerespons gekregen?**

a. JA - Ga door naar [Stap 4](#step-4).\
b. NO - Doorgaan naar [Stap 9](#step-9).

+++

## Stap 4 - verifieer de cluster van de Elasticsearch gezond {#step-4}

+++**Reactie groen?**

a. JA - Elasticsearch is beschikbaar voor de verwerking van gegevens en herindexering zou moeten werken. Doorgaan naar [Stap 5](#step-5).\
b. NO - Geel of rood betekent dat er problemen zijn met verbindingen tussen knooppunten en dat sommige gegevens mogelijk niet beschikbaar zijn. Indien geel, voer het bevel in: `php bin/magento config:show catalog/search/engine` om je zoekmachine te controleren. Doorgaan naar [Stap 6](#step-6). Indien rood, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Stap 5 - Verifieer het werk van het onderzoek {#step-5}

+++**Probleem zoeken?**

Symptomen kunnen geen producten, lege categorieën of geen updates van producten of productcategorieën bevatten zijn niet correct.

a. JA - Voer deze opdracht uit om de status van de zoekopdracht in de catalogus te controleren: `php bin/magento indexer:status`. Doorgaan naar [Stap 8](#step-8).\
b. NO - Run, opdracht: `php bin/magento config:show catalog/search/engine`. Doorgaan naar [Stap 6](#step-6).

+++

## Stap 6 - Controleer ElasticSuite {#step-6}

+++**ElasticSuite in gebruik?**

a. JA - Controleer of ElasticSuite de huidige versie heeft door deze opdracht uit te voeren: `cat composer.lock | grep -A 1 elasticsuite | grep '"version"'` Als u wilt controleren of deze versie wordt afgeschreven of aanbevolen, raadpleegt u [Github: Smile-SA/elaticsuite](https://github.com/Smile-SA/elasticsuite). Ga als ElasticSuite up-to-date is [Stap 10](#step-10).\
b) NEE - ga door met [Stap 7](#step-7).

+++

## Stap 7 - controleer de ECE-hulpmiddelen bijgewerkt {#step-7}

+++**Is ECE-tools de nieuwste versie?**

Voer de opdracht uit: `php ./vendor/bin/ece-tools -V` en controleer de versie ECE-tools. Is het [recentste versie van ECE-tools](https://github.com/magento/ece-tools/releases)?

a. JA - Ga door naar [Stap 5a](#step-5).\
b. NO - Upgrade ECE-tools naar de meest recente versie. De opdracht uitvoeren `php bin/magento config: show catalog/search/engine` om je zoekmachine te controleren. Doorgaan naar [Stap 6](#step-6).

+++

## Stap 8 - Controleren op opnieuw indexeren {#step-8}

+++**Zoekstatus van catalogus in _Verwerking_?**

a. JA - U moet wachten tot de verwerking is voltooid en vervolgens controleren of de productcategorieën zijn bijgewerkt. Zo niet, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Als de zoekstatus van de catalogus gelijk is aan _Opnieuw indexeren is vereist_ uitgevoerd in CLI/Terminal: `php bin/magento cron:run`. Als dit niet werkt, voert u het volgende uit: `php bin/magento indexer:reindex`. Als dit het probleem niet oplost, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Stap 9 - controleer uw configuratie {#step-9}

+++**`.yaml`bestand onlangs bijgewerkt?**

a. JA - Controle `.yaml` De configuratie van de Elasticsearch door naar DevDocs te verwijzen [Elasticsearch instellen: Elasticsearch inschakelen](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=elastic%20search%20yaml).\
b) NO - [Een ondersteuningsticket verzenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Stap 10 - Controleren op volgindices {#step-10}

+++**Worden er volgindices weergegeven?**

Uitvoeren `curl elasticsearch.internal:9200/_cat/indices` (als u zich op een integratiemilieu bevindt dat alle takken van de Aanzet omvat). Als u op Pro het opvoeren of productiemilieu loopt `curl localhost:9200/_cat/indices`. Worden er volgindices weergegeven? De uitvoer controleren voor`_tracking_log_`.

a. JA - Als u een versie van ElasticSuite gebruikt die ouder is dan versie 2.8.0, wordt aanbevolen [upgrade naar ElasticSuite 2.8.0 om de retentie van trackingindices aan te passen of om tracering uit te schakelen](https://support.magento.com/hc/en-us/articles/360035266131?). Als u niet onmiddellijk kunt upgraden, kunt u [een uitsnede maken om trackingindexen te verwijderen](/help/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.md). Dit kan echter prestatieproblemen veroorzaken. Nadat u de upgrade naar ElasticSuite 2.8.0 hebt uitgevoerd of trackingindexen hebt verwijderd, voert u de opdracht uit (als u zich in een Pro-testomgeving of een productieomgeving bevindt):`localhost:9200/_cat/allocation?v` om de beschikbare ruimte te controleren. Als u zich op één van de integratiemilieu&#39;s (die alle takken van de Aanzet omvatten) loopt `elasticsearch.internal:9200/_cat/allocation?v`. Doorgaan naar [Stap 11](#step-11).\
b. NO - Als u zich in een Pro-testomgeving of -productieomgeving bevindt, voert u `localhost:9200/_cat/allocation?v` en controleer de beschikbare ruimte. Als u zich op één van de integratiemilieu&#39;s (die alle takken van de Aanzet omvatten) loopt `elasticsearch.internal:9200/_cat/allocation?v`. Doorgaan naar [Stap 11](#step-11).

+++

## Stap 11 - Specifieke fout opzoeken {#step-11}

+++**Specifieke fout?**

Logbestanden, extensies en aangepaste code van Adobe Commerce en ES.

a. JA - Lees het artikel over probleemoplossing in het Adobe Commerce Help Center [Controleer of de Elasticsearch correct is geïnstalleerd](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) of [Bij gebruik van de ElasticSuite-plug-in loopt de Elasticsearch vast of heeft deze problemen onvoldoende geheugen](https://support.magento.com/hc/en-us/articles/360035266131).\
b. NO - Doorgaan naar [Stap 12](#step-12).

+++

## Stap 12 - Beschikbare opslag controleren {#step-12}

+++**Opslaggebruik > 85%?**

a. JA - U moet de beschikbare opslagruimte verhogen. Raadpleeg DevDocs[Elasticsearch instellen: Elasticsearch inschakelen](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=elastic%20search%20yaml). Voer vervolgens uit: `localhost:9200/_cat/allocation?v` (als u zich op Pro het opvoeren of productiemilieu&#39;s bevindt). Als u op één van de integratiemilieu&#39;s (die alle takken van de Aanzet omvatten) loopt: `elasticsearch.internal:9200/_cat/allocation?v`. Doorgaan naar [Stap 11](#step-11).\
b) NO - [Een ondersteuningsticket verzenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Terug naar stap 1](#step-1)
