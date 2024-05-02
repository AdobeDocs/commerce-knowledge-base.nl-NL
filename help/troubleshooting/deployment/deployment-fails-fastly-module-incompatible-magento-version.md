---
title: Implementatie mislukt snel incompatibele Adobe Commerce-versie
description: "BIJGEWERKT: 29 februari 2019"
exl-id: aab77407-94e5-42de-92f4-2f0c19e24fa4
feature: Deploy, Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Implementatie mislukt snel incompatibele Adobe Commerce-versie

BIJGEWERKT: 29 februari 2019

Dit artikel bevat een oplossing voor het geval de implementatie mislukt omdat de module Snelheid niet compatibel is met uw huidige Adobe Commerce-versie.

**Probleem:** De plaatsing ontbreekt na nieuw begaan en duw, met het foutenbericht gelijkend op het volgende:

>\[Exception\] Warning: Missing argument 3 for Fastly\\Cdn\\Plugin\\..., called in /app/vendor/magento/framework/Interception/Interceptor.php ... and defined in /app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php ...

**Oorzaak:** achterwaartse incompatibele wijzigingen in module Fastly v1.2.79.

**Oplossing (tijdelijk):** Upgrade de Fastly-module naar versie 1.2.82 of hoger en upload een nieuwe VCL in de Commerce Admin. Dan, verbind en duw uw veranderingen om een succesvolle plaatsing teweeg te brengen.

## Betrokken versies

* Adobe Commerce op locatie 2.1.X
* Adobe Commerce op cloudinfrastructuur 2.1.X
* Fastly module 1.2.79

## Probleem

Wanneer u begaan en uw veranderingen in de het Integreren, Productie, of het Staging milieu duwt, gewoonlijk brengt de volgende stap het plaatsingsproces in werking. Dit gebeurt automatisch in Adobe Commerce op de editie van de cloudinfrastructuur en handmatig in Adobe Commerce op locatie.

De plaatsing zou met de volgende foutenmeldingen kunnen ontbreken:

```
[2019-01-23 00:00:00] INFO: php ./bin/magento setup:static-content:deploy --ansi --no-interaction --jobs 1 --exclude-theme Magento/luma en_GB en_US
[2019-01-23 00:00:00] CRITICAL:
  Requested languages: en_GB, en_US
  Requested areas: frontend, adminhtml
  Requested themes: Magento/blank, Magento/backend
  === frontend -> Magento/blank -> en_GB ===

    [Exception]
    Warning: Missing argument 3 for Fastly\Cdn\Plugin\ExcludeFilesFromMinification::afterGetExcludes(), called in /app/vendor/magento/framework/Interception/Interceptor.php on line 152 and defined in /app/vendor/fastly/magento2/Plugin/ExcludeFilesFromMinification.php on line 38

  setup:static-content:deploy [-d|--dry-run] [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [-t|--theme[="..."]] [--exclude-theme[="..."]] [-l|--language[="..."]] [--exclude-language[="..."]] [-a|--area[="..."]] [--exclude-area[="..."]] [-j|--jobs[="..."]] [--symlink-locale] [languages1] ... [languagesN]

[2019-01-23 000:00:00] INFO: Set flag: var/.deploy_is_failed
[2019-01-23 00:00:00] CRITICAL: Command php ./bin/magento setup:static-content:deploy --ansi --no-interaction --jobs 1 --exclude-theme Magento/luma en_GB en_US returned code 1
```

Als u Adobe Commerce gebruikt voor de oplossing van de cloud-infrastructuur, wordt deze foutmelding weergegeven in het dialoogvenster [logboek implementeren](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html#log-deploy-log). Voor Adobe Commerce op-gebouw, zult u de fout in de bevellijn zien.

## Oorzaak

Dit probleem wordt veroorzaakt door de achterwaartse incompatibele wijzigingen in module Fastly v1.2.79.

## Oplossing

Voer een upgrade uit van de module Snelheid naar versie 1.2.82 of hoger.

Voer hiertoe de volgende stappen uit:

1. Voer een van de volgende opdrachten uit:
   * als de Fastly-module is opgenomen in het magento-cloud-metapakket:    <pre>composer update magento/magento-cloud-metapack</pre>
   * als de Fastly-module afzonderlijk is geïnstalleerd (bijvoorbeeld als u Adobe Commerce op locatie gebruikt, niet de cloud) <pre>composer-update snel/magento2</pre>
1. Leg de wijzigingen vast en duw deze op en activeer het implementatieproces als dit niet automatisch gebeurt.
1. In de Admin [uploadt de nieuwe VCL naar Snelst](https://devdocs.magento.com/guides/v2.3/cloud/cdn/configure-fastly.html#upload-vcl-snippets).
