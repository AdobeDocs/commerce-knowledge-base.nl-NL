---
title: .magento.env.yaml veranderingen niet getoond in env.php na opstelling
description: Dit artikel biedt een oplossing voor het probleem waarbij wijzigingen in het bestand .magento.env.yaml niet worden doorgevoerd in app/etc/env.php na de implementatie.
exl-id: 39ea7295-ba5a-40cc-bc68-a5e0b965c1a7
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# .magento.env.yaml veranderingen niet getoond in env.php na opstelling

>[!NOTE]
>
>Als dit probleem is, voert u een upgrade uit naar ece-tools 2002.1.5 om dit probleem op te lossen. 2002.1.5 heeft functionaliteit om opcache op elke plaatsing terug te stellen zodat is er nooit een behoefte om het plaatsen te veranderen `opcache.enable_cli=1`. Als u niet wilt bevorderen, dan zou u de tijdelijke stappen moeten doen zoals hieronder beschreven in de oplossing.

Dit artikel biedt een oplossing voor de kwestie waarin wijzigingen in `.magento.env.yaml` bestand wordt niet weerspiegeld in `app/etc/env.php` na de implementatie.

## Betrokken producten en versies

* Adobe Commerce over cloudinfrastructuur (alle [ondersteunde versies](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)).

## Probleem

Wijzigingen aangebracht in de `.magento.env.yaml` bestand heeft geen invloed op de `app/etc/env.php` gegenereerd.

<u>Stappen om te reproduceren:</u>

Een waarde wijzigen in `.magento.env.yaml` en naar de server te duwen, waar de configuratie (en plaatsingsmontages) voor het momenteel uitgecheckte milieu zou moeten bepalen. Zie voor stappen [Omgevingsvariabelen > Variabelen implementeren](https://devdocs.magento.com/cloud/env/variables-deploy.html) in onze ontwikkelaarsdocumentatie.

<u>Verwacht resultaat:</u>

Wijzigingen aangebracht in de `.magento.env.yaml` bestand heeft invloed op `app/etc/env.php` gegenereerd.

<u>Werkelijk resultaat:</u>

De wijzigingen hebben geen invloed op de `app/etc/env.php` variabelen na implementatie.

## Oorzaak

Dit probleem kan worden veroorzaakt door de onjuiste waarde van het `opcache.enable_cli` in de `php.ini` bestand.

## Oplossing

1. Controleer of het systeem is geconfigureerd volgens [Aanbevolen procedures voor Adobe Commerce-prestaties > Softwareaanbevelingen](https://devdocs.magento.com/guides/v2.4/performance-best-practices/software.html).
1. Controleren of `opcache.enable_cli` richtlijn in `php.ini` is ingesteld op `0` door uitvoering: `php -i | grep opcache.enable_cli`
1. Als de uitvoer er zo uitziet `opcache.enable_cli=1` , bewerkt u de `php.ini` bestand in de hoofdmap van het project en wijzigen `opcache.enable_cli=1` tot `opcache.enable_cli=0`
1. Implementeer het project opnieuw.

## Gerelateerde lezing

* [Cloud voor Adobe Commerce > Samenstellen en implementeren](https://devdocs.magento.com/cloud/project/magento-env-yaml.html).
