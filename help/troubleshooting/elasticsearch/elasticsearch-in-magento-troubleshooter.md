---
title: Elasticsearch in Adobe Commerce probleemoplosser
description: Problemen met de Elasticsearch in Adobe Commerce kunnen worden opgelost met het hulpprogramma voor het oplossen van problemen met Elasticsearch. Klik op elke vraag om het antwoord in elke stap van de probleemoplosser te onthullen.
exl-id: acae0da0-2918-4021-9fbe-c138940c5a72
feature: Categories
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 0%

---

# Elasticsearch in Adobe Commerce probleemoplosser

Problemen met de Elasticsearch in Adobe Commerce kunnen worden opgelost met het hulpprogramma voor het oplossen van problemen met Elasticsearch. Klik op elke vraag om het antwoord in elke stap van de probleemoplosser te onthullen.

>[!WARNING]
>
>Op Adobe Commerce over cloudinfrastructuur dient u te weten dat serviceupgrades niet naar de productieomgeving kunnen worden doorgevoerd zonder dat ons infrastructuurteam hiervan 48 uur op de hoogte wordt gesteld. Dit is nodig omdat wij ervoor moeten zorgen dat wij een ingenieur van de infrastructuursteun beschikbaar hebben om uw configuratie binnen een gewenst tijdsbestek met minimale onderbreking aan uw productiemilieu bij te werken. Zo 48 uren voorafgaand aan wanneer uw veranderingen op productie moeten zijn [ een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voorleggen detailend uw vereiste de dienstverbetering en het verklaren van de tijd wanneer u het verbeteringsproces wilt beginnen.

## Stap 1 - Controleren op probleem met Elasticsearch {#step-1}

+++**kon uw probleem op Elasticsearch betrekking hebben?**

De kwesties van de Elasticsearch die door foutenmeldingen worden vermeld, &quot;_Geen levende knopen die in uw cluster&quot;worden gevonden,_ ontbrekende producten, en de vertoning van oude productinformatie.

a. JA - ga aan [ Stap 2 ](#step-2) te werk.\
b. NO - Onderzoek opnieuw op relevante onderzoekstermijnen in de [ Kennisbank van het Centrum van de Hulp van Adobe Commerce ](https://support.magento.com/hc).

+++

## Stap 2 - Controleren op installatieprobleem {#step-2}

+++**is het een nieuwe installatie van Elasticsearch?**

a. JA - [ Zorg ervoor dat de Elasticsearch correct is geïnstalleerd.](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) Controleer ook of u zich op Adobe Commerce op cloudinfrastructuur 2.3.1 of hoger bevindt. Handelaren die een upgrade naar Adobe Commerce hebben uitgevoerd op een cloudinfrastructuur (versie 2.3.1 en hoger) en die een versie van Elasticsearch hebben die ouder is dan 6.x, kunnen fouten ondervinden bij de implementatie. Om deze kwestie op te lossen moeten de de cliëntmodule en dienst van de Elasticsearch van de Elasticsearch op de recentste geadviseerde versies zijn. Voor stappen verwijzen naar [ kwesties van de Elasticsearch na Adobe Commerce op wolkeninfrastructuur 2.3.1+ verbetering ](/help/troubleshooting/elasticsearch/elasticsearch-issues-after-magento-commerce-cloud-2-3-1-upgrade.md).\
b. NO - Controleer de gezondheid van uw cluster. Voer deze opdracht uit als u zich in een Pro-testomgeving of -productieomgeving bevindt: `curl -m1 localhost:9200/_cluster/health?pretty`. Voer `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty` uit als u zich in een integratieomgeving bevindt (die alle vertakkingen Starter bevat). Ga aan [ Stap 3 ](#step-3) te werk.

+++

## Stap 3 - controleer of de cluster Elasticsearch beschikbaar is {#step-3}

+++**Heb u een reactie van de Dienst gekregen?**

a. JA - ga aan [ Stap 4 ](#step-4) te werk.\
b. NO - ga aan [ Stap 9 ](#step-9) te werk.

+++

## Stap 4 - verifieer de cluster van de Elasticsearch gezond {#step-4}

+++**groene Reactie?**

a. JA - Elasticsearch is beschikbaar voor de verwerking van gegevens en herindexering zou moeten werken. Ga aan [ Stap 5 ](#step-5) te werk.\
b. NO - Geel of rood betekent dat er problemen zijn met verbindingen tussen knooppunten en dat sommige gegevens mogelijk niet beschikbaar zijn. Als geel, stel het bevel: `php bin/magento config:show catalog/search/engine` in werking om uw onderzoeksmotor te controleren. Ga aan [ Stap 6 ](#step-6) te werk. Als rood, [ een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voorleggen.

+++

## Stap 5 - Verifieer het werk van het onderzoek {#step-5}

+++**Uitgave van het Onderzoek?**

Symptomen kunnen geen producten, lege categorieën of geen updates van producten of productcategorieën bevatten zijn niet correct.

a. JA - Voer deze opdracht uit om de status van de zoekopdracht in de catalogus te controleren: `php bin/magento indexer:status` . Ga aan [ Stap 8 ](#step-8) te werk.\
b. NO - Run, opdracht: `php bin/magento config:show catalog/search/engine`. Ga aan [ Stap 6 ](#step-6) te werk.

+++

## Stap 6 - Controleer ElasticSuite {#step-6}

+++**ElasticSuite in gebruik?**

a. JA - controleer als ElasticSuite bij de huidige versie door dit bevel in werking te stellen is: `cat composer.lock | grep -A 1 elasticsuite | grep '"version"'` om te controleren of deze versie wordt afgeschreven of geadviseerd, verwijs naar [ Github: Smile-SA/elaticsuite ](https://github.com/Smile-SA/elasticsuite). Als ElasticSuite bijgewerkt is ga aan [ Stap 10 ](#step-10) te werk.\
b. NO - ga aan [ Stap 7 ](#step-7) te werk.

+++

## Stap 7 - controleer de ECE-hulpmiddelen bijgewerkt {#step-7}

+++**is ECE-hulpmiddelen de recentste versie?**

Voer de opdracht `php ./vendor/bin/ece-tools -V` uit en controleer de versie van ECE-tools. Is het de [ recentste versie van ECE-hulpmiddelen ](https://github.com/magento/ece-tools/releases)?

a. JA - ga aan [ Stap 5a ](#step-5) te werk.\
b. NO - Upgrade ECE-tools naar de meest recente versie. Voer de opdracht `php bin/magento config: show catalog/search/engine` uit om uw zoekmachine te controleren. Ga aan [ Stap 6 ](#step-6) te werk.

+++

## Stap 8 - Controleren op opnieuw indexeren {#step-8}

+++**is de status van het catalogusonderzoek in _Verwerking_?**

a. JA - U moet wachten tot de verwerking is voltooid en vervolgens controleren of de productcategorieën zijn bijgewerkt. Als zij niet, [ een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voorleggen.\
b. NO - als het statuut van catalogusonderzoek _vereist opnieuw indexeren_ in CLI/Terminal: `php bin/magento cron:run` is. Als dit niet werkt, voert u: `php bin/magento indexer:reindex` uit. Als dit niet de kwestie oplost, [ voorlegt een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Stap 9 - controleer uw configuratie {#step-9}

+++**`.yaml`bestand onlangs bijgewerkt?**

a. JA - de configuratie van de Elasticsearch van de Controle `.yaml` door naar DevDocs [ Elasticsearch van de Opstelling te verwijzen: Om Elasticsearch ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch) toe te laten.\
b. NO - [ voorlegt een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Stap 10 - Controleren op volgindices {#step-10}

+++**zijn er het volgen indexen vermeld?**

Voer `curl elasticsearch.internal:9200/_cat/indices` uit (als u zich op een integratieomgeving bevindt die alle vertakkingen Starter bevat). Voer `curl localhost:9200/_cat/indices` uit als u op een Pro-testomgeving of -productieomgeving werkt. Worden er volgindices weergegeven? Controleer de output voor `_tracking_log_`.

a. JA - als u op een versie van ElasticSuite voorafgaand aan versie 2.8.0 bent, adviseert men dat u [ verbetering aan ElasticSuite 2.8.0 aanbeveelt om het volgen indexenbehoud aan te passen of het volgen onbruikbaar te maken ](https://support.magento.com/hc/en-us/articles/360035266131?). Als u niet kunt onmiddellijk bevorderen kunt u [ tot een kruin leiden om het volgen indexen ](/help/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.md) te verwijderen. Dit kan echter prestatieproblemen veroorzaken. Zodra u aan ElasticSuite 2.8.0 hebt bevorderd of verwijder het volgen indices in werking stelt het bevel (als u op Pro het opvoeren of productiemilieu&#39;s bent):`localhost:9200/_cat/allocation?v` om beschikbare ruimte te controleren. Voer `elasticsearch.internal:9200/_cat/allocation?v` uit als u zich in een van de integratieomgevingen bevindt (die alle Starter-vertakkingen bevat). Ga aan [ Stap 11 ](#step-11) te werk.\
b. NO - Als u zich in een Pro-testomgeving of een productieomgeving bevindt, voert u `localhost:9200/_cat/allocation?v` uit en controleert u de beschikbare ruimte. Voer `elasticsearch.internal:9200/_cat/allocation?v` uit als u zich in een van de integratieomgevingen bevindt (die alle Starter-vertakkingen bevat). Ga aan [ Stap 11 ](#step-11) te werk.

+++

## Stap 11 - Specifieke fout opzoeken {#step-11}

+++**Specifieke fout?**

Logbestanden, extensies en aangepaste code van Adobe Commerce en ES.

a. JA - herzie het artikel van het Oplossen van problemen van het Centrum van de Hulp van Adobe Commerce [ ervoor zorgen de Elasticsearch behoorlijk ](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md) wordt geïnstalleerd of [ de Elasticsearch crasht of heeft uit geheugenkwesties wanneer het gebruiken van de insteekmodule ElasticSuite ](https://support.magento.com/hc/en-us/articles/360035266131).\
b. NO - ga aan [ Stap 12 ](#step-12) te werk.

+++

## Stap 12 - Beschikbare opslag controleren {#step-12}

+++**gebruik van de Opslag > 85%?**

a. JA - U moet de beschikbare opslagruimte verhogen. Verwijs naar DevDocs [ Elasticsearch van de Opstelling: Om Elasticsearch ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch) toe te laten. Voer vervolgens uit: `localhost:9200/_cat/allocation?v` (als u zich op een testomgeving of een productieomgeving met Pro bevindt). Als u zich op een van de integratieomgevingen bevindt (die alle Starter-vertakkingen bevat), voert u het volgende uit: `elasticsearch.internal:9200/_cat/allocation?v`. Ga aan [ Stap 11 ](#step-11) te werk.\
b. NO - [ voorlegt een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Terug naar stap 1](#step-1)
