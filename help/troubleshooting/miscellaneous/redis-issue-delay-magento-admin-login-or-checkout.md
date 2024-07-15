---
title: Uitgave opnieuw vertragen Aanmelden bij Commerce Admin of uitchecken
description: Dit artikel bevat een oplossing voor het probleem wanneer u zich aanmeldt bij de Commerce Admin of wanneer u de uitcheckpagina opent. Dit veroorzaakt vertraging of time-out (meer dan 30 seconden). De kwestie komt voor wanneer Redis voor zittingsopslag wordt gebruikt.
exl-id: a91a7a51-7cc4-4910-a9de-3a212788663f
feature: Admin Workspace, Checkout, Orders, Services
role: Developer
source-git-commit: aa8c32e3524d669daea7bcf8bc63ed9f8ed16ffa
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Uitgave opnieuw vertragen Aanmelden bij Commerce Admin of uitchecken

Dit artikel bevat een oplossing voor het probleem wanneer u zich aanmeldt bij de Commerce Admin of wanneer u de uitcheckpagina opent. Dit veroorzaakt vertraging of time-out (meer dan 30 seconden). De kwestie komt voor wanneer Redis voor zittingsopslag wordt gebruikt.

**Oorzaak:**   [ Uitgave van Github \#12385 ](https://github.com/magento/magento2/issues/12385).

**Oplossing:** update aan het recentste flard van Adobe Commerce om deze kwesties voor alle versies van Redis en specifieke versies van Adobe Commerce te bevestigen.

## Betrokken versies en technologieën

* Adobe Commerce op cloudinfrastructuur versie 2.1.11 - 2.1.13 en 2.2.1
* Adobe Commerce-versies ter plaatse 2.1.11 - 2.1.13 en 2.2.1
* Redis, alle versies

Als u Adobe Commerce op versie van de wolkeninfrastructuur [ 2.2.0 ](#h_64593789291526919876198) gebruikt, is een oplossing beschikbaar.

## Probleem

Aanmelden bij Commerce Admin of doorgaan naar de afhandelingspagina duurt meer dan 30 seconden.

Dit gebeurt alleen als gebruikerssessies worden opgeslagen in Redis.

## Oorzaak

Adobe Commerce had een probleem met het mechanisme voor sessievergrendeling dat een time-out van 30 seconden toevoegde aan bepaalde bewerkingen toen Redis werd gebruikt voor sessieopslag. Voor details, zie de [ kwestie van Github \#12385 ](https://github.com/magento/magento2/issues/12385).

Dit probleem is opgelost in Adobe Commerce 2.1.14 en 2.2.2.

## Oplossingen: patch of upgrade

### Oplossing 1: De pleister aanbrengen met een oplossing

Om een flard te ontvangen, [ voorlegt een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) verzoekend het flard. Geef in uw ticket uw Adobe Commerce-versie en het bijbehorende referentienummer voor de patch op:

* **2.1.11 en later:** MDVA-7835
* **2.2.1:** MDVA-8128

Het algemene (version-agnostic) referentienummer is MAGETWO-84289.

### Oplossing 2: upgrade naar 2.1.14/2.2.2 of hoger

Als u eerder hebt overwogen een upgrade naar Adobe Commerce 2.2.2 of hoger uit te voeren, kunt u deze update gebruiken om het probleem op te lossen.

## Oplossing: sessievergrendeling uitschakelen

Als u de sessievergrendeling wilt uitschakelen, stelt u `disable_locking` in op `1` in de configuratiesectie Opnieuw van het `env.php` -bestand:

```php
'session' =>
  array (
    'save' => 'redis',
    'redis' =>
    array (
      'host' => 'redis.internal',
      'port' => 6379,
      'database' => '0',
      'disable_locking' => '1'
    ),
  ),
```

Deze oplossing heeft geen invloed op andere Adobe Commerce-functionaliteit.

### De tijdelijke oplossing herstellen nadat de patch is toegepast

Nadat u de patch met de fix hebt toegepast, is de tijdelijke oplossing niet meer nodig. U kunt de patch dus weer instellen op `disable_locking` . `0`

## Adobe Commerce on cloud Infrastructure 2.2.0: gebruik ECE-Tools v2002.0.8 of hoger {#h_64593789291526919876198}

Het [ ECE-Hulpmiddelen ](https://devdocs.magento.com/cloud/project/ece-tools-update.html) pakket van het plaatsingsmanuscript met versies 2002.0.3 - 2002.0.7 [ past ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) automatisch de tijdelijke oplossing toe, die `disable_locking` aan `1` plaatst. Hierdoor wordt het mechanisme voor sessievergrendeling uitgeschakeld voor Adobe Commerce 2.2.0, waarop het oorspronkelijke probleem zich niet voordoet.

Als u Adobe Commerce uitvoert op cloudinfrastructuur 2.2.0, moet u ECE-Tools upgraden naar versie 2002.0.8 of hoger. U kunt ook overwegen om uw Adobe Commerce op cloudinfrastructuur te upgraden naar versie 2.2.2 of hoger.
