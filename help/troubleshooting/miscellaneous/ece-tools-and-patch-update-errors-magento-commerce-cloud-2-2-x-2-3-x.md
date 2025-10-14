---
title: ECE-tools en patchupdatefouten Adobe Commerce cloud Infrastructure 2.2.x, 2.3.x
description: Dit artikel biedt een oplossing voor het probleem waarbij foutberichten worden weergegeven zoals "*kan de stream niet openen:*" of "*Dit bestand of deze map is niet beschikbaar*" wanneer u probeert updates te implementeren naar ECE-gereedschappen, patches of andere wijzigingen.
exl-id: b1658001-0ffd-4f8a-a15f-d785efcee51f
feature: Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# ECE-tools en patchupdatefouten Adobe Commerce cloud Infrastructure 2.2.x, 2.3.x

Dit artikel verstrekt een oplossing voor de kwestie waar u foutenmeldingen met inbegrip van &quot;*ontbrak om stroom te openen:*&quot; of &quot;*geen dergelijk dossier of folder*&quot;wanneer het proberen om updates aan ECE-Hulpmiddelen, flarden of andere veranderingen op te stellen.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur 2.2.x, 2.3.x

## Probleem

Fouten bij het implementeren van updates voor ECE-tools, patches of andere wijzigingen zijn onder andere: PHP-fouten in de Cloud Console en in de `var/log/cloud.log`

```
W: PHP Warning: require(<path to file>): failed to open stream: No such file or directory in <path to file> on line 70
W: PHP Fatal error: require(): Failed opening required '<path to file>;'
(include_path='<path to file>') in <path to file> on line 70

Warning: require(/app/vendor/composer/../../app/etc/NonComposerComponentRegistration.php):
failed to open stream: No such file or directory in /app/vendor/composer/autoload_real.php
on line 70

Fatal error: require(): Failed opening required '/app/vendor/composer/../../app/etc/NonComposerComponentRegistration.php'
(include_path='/app/vendor/magento/zendframework1/library:.:/usr/share/php')
in /app/vendor/composer/autoload_real.php on line 70

E: Error building project: Step failed with status code 255.
```

Fouten in uitzonderingslogbestand:

```
CRITICAL:
error: <path to missing file>: No such file or directory
```

```
W: Generating optimized autoload files
W: PHP Warning: Uncaught ErrorException: require(<path to file>):
failed to open stream: No such file or directory in <path to file>
```

```
PHP Warning: Uncaught Exception: Warning: require(/app/setup/config/application.config.php):
failed to open stream: No such file or directory in /app/vendor/magento/framework/Console/Cli.php
on line 63 in /app/vendor/magento/framework/App/ErrorHandler.php:61
```

```
[Symfony\Component\Console\Exception\CommandNotFoundException]
 W: There are no commands defined in the "module" namespace.
```

## Oorzaak

Onjuiste configuratie van het `composer.json` -bestand.

## Oplossing

Als een instelling ontbreekt in uw `composer.json` -bestand, worden sommige mappen niet gekopieerd uit de Adobe Commerce Code Base. Het pakket en de update/patch kunnen niet worden toegepast omdat er geen bestanden worden gevonden.

Wijzig de extra sectie zodat deze overeenkomt met de onderstaande sectie en probeer de implementatie opnieuw uit te voeren.

```
"extra":{
  "magento-force": true,
  "magento-deploystrategy": "copy"
}
```

## Gerelateerde lezing

* [&#x200B; Verbeteringen en flarden &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/best-practices) in onze ontwikkelaardocumentatie.
