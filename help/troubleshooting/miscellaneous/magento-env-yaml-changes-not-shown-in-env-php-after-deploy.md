---
title: .magento.env.yaml veranderingen niet getoond in env.php na opstelling
description: Dit artikel biedt een oplossing voor het probleem waarbij wijzigingen in het bestand .magento.env.yaml niet worden doorgevoerd in app/etc/env.php na de implementatie.
exl-id: 39ea7295-ba5a-40cc-bc68-a5e0b965c1a7
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# .magento.env.yaml veranderingen niet getoond in env.php na opstelling

>[!NOTE]
>
>Als dit probleem is, voert u een upgrade uit naar ece-tools 2002.1.5 om dit probleem op te lossen. 2002.1.5 heeft functionaliteit om opcache bij elke plaatsing opnieuw in te stellen zodat er nooit een behoefte is om het plaatsen `opcache.enable_cli=1` te veranderen. Als u niet wilt bevorderen, dan zou u de tijdelijke stappen moeten doen zoals hieronder beschreven in de oplossing.

Dit artikel biedt een oplossing voor het probleem waarbij wijzigingen in het `.magento.env.yaml` -bestand niet worden doorgevoerd in `app/etc/env.php` na de implementatie.

## Betrokken producten en versies

* Adobe Commerce op wolkeninfrastructuur (alle [ gesteunde versies ](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)).

## Probleem

Wijzigingen die u aanbrengt in het `.magento.env.yaml` -bestand hebben geen invloed op de gegenereerde `app/etc/env.php` .

<u> Stappen om te reproduceren:</u>

Wijzig elke waarde in `.magento.env.yaml` en druk naar de server, waar deze de configuratie (en implementatie-instellingen) voor de momenteel uitgecheckte omgeving moet definiëren. Voor stappen, zie [ Variabelen van het Milieu > Variabelen opstelt ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy) in onze ontwikkelaarsdocumentatie.

<u> Verwacht resultaat:</u>

Wijzigingen die in het `.magento.env.yaml` -bestand worden aangebracht, zijn van invloed op de gegenereerde `app/etc/env.php` .

<u> Ware resultaat:</u>

De wijzigingen hebben na de implementatie geen invloed op de variabelen van `app/etc/env.php` .

## Oorzaak

Het probleem kan worden veroorzaakt door de onjuiste waarde van de parameter `opcache.enable_cli` in het `php.ini` -bestand.

## Oplossing

1. Controleer dat het systeem volgens [ Beste praktijken van de Prestaties van Adobe Commerce > de aanbevelingen van de Software ](https://experienceleague.adobe.com/nl/docs/commerce-operations/performance-best-practices/software) wordt gevormd.
1. Controleer of de aanwijzing `opcache.enable_cli` in `php.ini` is ingesteld op `0` door het volgende uit te voeren: `php -i | grep opcache.enable_cli`
1. Als de uitvoer er als `opcache.enable_cli=1` uitziet, bewerkt u het `php.ini` -bestand in de hoofdmap van het project en wijzigt u `opcache.enable_cli=1` in `opcache.enable_cli=0`
1. Implementeer het project opnieuw.

## Gerelateerde lezing

* [ Wolk voor Adobe Commerce > bouwt en stelt ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml) op.
