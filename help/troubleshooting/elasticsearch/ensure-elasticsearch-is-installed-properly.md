---
title: Controleer of de Elasticsearch correct is geïnstalleerd
description: In dit artikel wordt gesproken over oplossingen voor problemen die worden veroorzaakt door een onjuiste installatie en configuratie van de Elasticsearch (ES).
exl-id: d2c5971c-4db4-4857-ae79-970313bce981
feature: Install
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Controleer of de Elasticsearch correct is geïnstalleerd

In dit artikel wordt gesproken over oplossingen voor problemen die worden veroorzaakt door een onjuiste installatie en configuratie van de Elasticsearch (ES).

>[!WARNING]
>
>Op Adobe Commerce over cloudinfrastructuur dient u te weten dat serviceupgrades niet naar de productieomgeving kunnen worden doorgevoerd zonder dat ons infrastructuurteam hiervan 48 uur op de hoogte wordt gesteld. Dit is nodig omdat wij ervoor moeten zorgen dat wij een ingenieur van de infrastructuursteun beschikbaar hebben om uw configuratie binnen een gewenst tijdsbestek met minimale onderbreking aan uw productiemilieu bij te werken. Zo 48 uren voorafgaand aan wanneer uw veranderingen op productie moeten zijn, [&#x200B; voorlegt een steunkaartje &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) detailerend uw vereiste de dienstverbetering en het verklaren van de tijd wanneer u het verbeteringsproces wilt beginnen.

## Elasticsearch versiecompatibiliteit met Adobe Commerce

* Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur:
   * v2.2.3+ ondersteunt ES 5.x
   * v2.2.8+ en v2.3.1+ ondersteunen ES 6.x
   * ES v2.x en v5.x worden niet geadviseerd wegens [&#x200B; Eind van Leven &#x200B;](https://www.elastic.co/support/eol). Nochtans, als u Adobe Commerce v2.3.1 hebt en ES 2.x of ES 5.x wilt gebruiken, moet u [&#x200B; de Elasticsearch veranderen php Cliënt &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/search/overview-search).
* Magento Open Source v2.3.0+ ondersteunt ES 5.x en 6.x (maar 6.x wordt aanbevolen).

## Probleem

De volgende symptomen wijzen erop dat de Elasticsearch niet correct wordt gevormd:

* `Error: No alive nodes in your cluster` - deze fout kan worden weergegeven in Adobe Commerce-logboeken:
   * `var/log/system.log`
   * `var/log/support_report.log`
   * `var/log/cron.log`
   * `var/log/exception.log`
   * of in de prompt (wanneer u bijvoorbeeld een redex uitvoert)
* Fouten die aangeven dat de versie van de Elasticsearch niet compatibel is met uw huidige versie van Adobe Commerce (dit is een specifieke fout voor de infrastructuur van de Adobe Commerce voor de cloud):

  ```
  [YYYY-MM-DD HH:MM:SS] CRITICAL: Fix configuration with given suggestions:    - Elasticsearch version #<version> is not compatible with current version of magento    Upgrade elasticsearch version to ~5.0
  ```

Waar *versie* de Dienst is die van de Elasticsearch op het wolkenmilieu loopt.

## Oorzaak

Elasticsearch is niet correct geïnstalleerd. Dit kan te wijten zijn aan:

* Een typefout in het configuratiebestand.
* Een versie in het configuratiebestand die niet overeenkomt met een versie van de Elasticsearch die voor de omgeving is geïnstalleerd.
* Een versie die correct in het milieu geïnstalleerd is, correct gevormd in het configuratiedossier, maar is geen gesteunde versie voor de momenteel geïnstalleerde versie van Adobe Commerce.

## Oplossing

Elasticsearch correct instellen:

* De handelaren op Adobe Commerce op wolkeninfrastructuur kunnen de stappen in onze ontwikkelaardocumentatie volgen: [&#x200B; de dienst van de Elasticsearch van de opstelling &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch).
* De handelaren op Adobe Commerce op-gebouw en de Magento Open Source kunnen de stappen in onze ontwikkelaarsdocumentatie volgen: [&#x200B; installeren en vormen Elasticsearch &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/search/overview-search).

Nadat u opstelling Elasticsearch hebt, controleer dat het correct is gevormd:

1. Meld u aan bij uw server.
1. Controleer het versienummer van de Elasticsearch (2.x, 5.x of 6.x) in de uitvoer van het uitvoeren van de opdracht: `curl -XGET <Elasticsearch hostname>:<Elasticsearch server port>` Bijvoorbeeld in Adobe Commerce op cloudinfrastructuur: `curl -XGET localhost:9200`
1. Ga als volgt te werk om te controleren wat er in Adobe Commerce is geconfigureerd in de configuratie van de cloud-infrastructuur: `php bin/magento config:show catalog/search`
1. Controleer `catalog/search/engine` en controleer of deze overeenkomt met het versienummer van de Elasticsearch. Bijvoorbeeld in Adobe Commerce op cloudinfrastructuur:
   * Elasticsearch 5.X - elasticsearch5
   * Elasticsearch 6.X - elasticsearch6
   * Elasticsearch 2.X - elasticsearch
1. Schakel `index_prefix` in. Als u meerdere omgevingen hebt, moet u ervoor zorgen dat er verschillende `index_prefix` -waarden voor zijn.
