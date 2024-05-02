---
title: Fout tijdens implementatie bij upgrade naar versie die PHP 8.1 ondersteunt
description: Dit artikel biedt een oplossing voor de fout die optreedt tijdens de implementatie bij de upgrade naar een versie die PHP 8.1 ondersteunt.
exl-id: bdc4a355-4f2b-49a7-9c5d-63c950f7ca30
feature: Deploy, Observability
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Fout tijdens implementatie bij upgrade naar versie die PHP 8.1 ondersteunt

Dit artikel biedt een oplossing voor de fout die optreedt tijdens de implementatie bij de upgrade naar een versie die PHP 8.1 ondersteunt.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur 2.4.4 en hoger

* Uitbreiding of technologie (snelweg, New Relic, enz.) versie PHP 8.1

## Probleem

De volgende fout treedt op tijdens de implementatie wanneer u een upgrade uitvoert naar een versie die PHP 8.1 ondersteunt.

```PHP
{{E: Error parsing configuration files:

applications: Uncaught exception: The "json" extension is not supported for php:8.1
at <script>:109:12
throw("The \"" + unsupported_extensions[0] + "\" extension is not supported for " + service.type);
^
E: Error: Invalid configuration files, aborting build}}
```

## Oorzaak

PHP 8.1 biedt al JSON-ondersteuning en vereist niet dat de extensie afzonderlijk wordt geïnstalleerd.

## Oplossing

JSON verwijderen uit de **Runtime** > **Extensies** sectie in `.magento.app.yaml` en opnieuw implementeren.

## Gerelateerde lezing

[PHP-toepassing](https://devdocs.magento.com/cloud/project/magento-app-php-application.html) in onze ontwikkelaarsdocumentatie.
