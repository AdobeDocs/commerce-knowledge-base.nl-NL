---
title: Controleer of de Elasticsearch correct is geïnstalleerd
description: In dit artikel wordt gesproken over oplossingen voor problemen die worden veroorzaakt door een onjuiste installatie en configuratie van de Elasticsearch (ES).
exl-id: d2c5971c-4db4-4857-ae79-970313bce981
feature: Install
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Controleer of de Elasticsearch correct is geïnstalleerd

In dit artikel wordt gesproken over oplossingen voor problemen die worden veroorzaakt door een onjuiste installatie en configuratie van de Elasticsearch (ES).

>[!WARNING]
>
>Op Adobe Commerce over cloudinfrastructuur dient u te weten dat serviceupgrades niet naar de productieomgeving kunnen worden doorgevoerd zonder dat ons infrastructuurteam hiervan 48 uur op de hoogte wordt gesteld. Dit is nodig omdat wij ervoor moeten zorgen dat wij een ingenieur van de infrastructuursteun beschikbaar hebben om uw configuratie binnen een gewenst tijdsbestek met minimale onderbreking aan uw productiemilieu bij te werken. Dus 48 uur voor het moment dat uw veranderingen in productie moeten zijn, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) het gedetailleerd van uw vereiste de dienstverbetering en het verklaren van de tijd wanneer u het verbeteringsproces wilt beginnen.

## Elasticsearch versiecompatibiliteit met Adobe Commerce

* Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur:
   * v2.2.3+ ondersteunt ES 5.x
   * v2.2.8+ en v2.3.1+ ondersteunen ES 6.x
   * ES v2.x en v5.x worden niet aanbevolen vanwege [Einde van levensduur](https://www.elastic.co/support/eol). Als u echter Adobe Commerce v2.3.1 hebt en ES 2.x of ES 5.x wilt gebruiken, moet u [De Elasticsearch-php-client wijzigen](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html).
* Magento Open Source v2.3.0+ ondersteunt ES 5.x en 6.x (maar 6.x wordt aanbevolen).

## Probleem

De volgende symptomen wijzen erop dat de Elasticsearch niet correct wordt gevormd:

* `Error: No alive nodes in your cluster` - deze fout kan in de logboeken van Adobe Commerce verschijnen:
   * `var/log/system.log`
   * `var/log/support_report.log`
   * `var/log/cron.log`
   * `var/log/exception.log`
   * of in de prompt (wanneer u bijvoorbeeld een redex uitvoert)
* Fouten die aangeven dat de versie van de Elasticsearch niet compatibel is met uw huidige versie van Adobe Commerce (dit is een specifieke fout voor de infrastructuur van de Adobe Commerce voor de cloud):

  ```
  [YYYY-MM-DD HH:MM:SS] CRITICAL: Fix configuration with given suggestions:    - Elasticsearch version #<version> is not compatible with current version of magento    Upgrade elasticsearch version to ~5.0
  ```

Wanneer *versie* is de Elasticsearch Service die wordt uitgevoerd in de cloud-omgeving.

## Oorzaak

Elasticsearch is niet correct geïnstalleerd. Dit kan te wijten zijn aan:

* Een typefout in het configuratiebestand.
* Een versie in het configuratiebestand die niet overeenkomt met een versie van de Elasticsearch die voor de omgeving is geïnstalleerd.
* Een versie die correct in het milieu geïnstalleerd is, correct gevormd in het configuratiedossier, maar is geen gesteunde versie voor de momenteel geïnstalleerde versie van Adobe Commerce.

## Oplossing

Elasticsearch correct instellen:

* Handelaars op Adobe Commerce op cloudinfrastructuur kunnen de stappen in onze ontwikkelaarsdocumentatie volgen: [Service Elasticsearch instellen](https://devdocs.magento.com/guides/v2.3/cloud/project/project-conf-files_services-elastic.html).
* Handelaren op Adobe Commerce op locatie en Magento Open Source kunnen de stappen in onze documentatie voor ontwikkelaars volgen: [Elasticsearch installeren en configureren](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html).

Nadat u opstelling Elasticsearch hebt, controleer dat het correct is gevormd:

1. Meld u aan bij uw server.
1. Controleer het versienummer van de Elasticsearch (2.x, 5.x, of 6.x) in de uitvoer van het uitvoeren van de opdracht: `curl -XGET <Elasticsearch hostname>:<Elasticsearch server port>` Bijvoorbeeld in Adobe Commerce op cloudinfrastructuur: `curl -XGET localhost:9200`
1. Controleer wat in Adobe Commerce op de Configuratie van de wolkeninfrastructuur door het bevel in werking te stellen wordt gevormd: `php bin/magento config:show catalog/search`
1. Controleren `catalog/search/engine` en zorg ervoor dat deze overeenkomt met het versienummer van de Elasticsearch. Bijvoorbeeld in Adobe Commerce op cloudinfrastructuur:
   * Elasticsearch 5.X - elasticsearch5
   * Elasticsearch 6.X - elasticsearch6
   * Elasticsearch 2.X - elasticsearch
1. Controleren `index_prefix`. Als u meerdere omgevingen hebt, moet u ervoor zorgen dat u verschillende `index_prefix` waarden voor deze groepen.
