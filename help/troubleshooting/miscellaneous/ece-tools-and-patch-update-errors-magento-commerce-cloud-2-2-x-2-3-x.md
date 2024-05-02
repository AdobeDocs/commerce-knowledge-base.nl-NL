---
title: ECE-tools en patchupdatefouten Adobe Commerce cloud Infrastructure 2.2.x, 2.3.x
description: Dit artikel biedt een oplossing voor het probleem waarbij foutberichten worden weergegeven zoals "*kan de stream niet openen:*" of "*Dit bestand of deze map is niet beschikbaar*" wanneer u probeert updates te implementeren naar ECE-gereedschappen, patches of andere wijzigingen.
exl-id: b1658001-0ffd-4f8a-a15f-d785efcee51f
feature: Cloud, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# ECE-tools en patchupdatefouten Adobe Commerce cloud Infrastructure 2.2.x, 2.3.x

Dit artikel biedt een oplossing voor het probleem waarbij foutberichten worden weergegeven, zoals &quot;*kan stroom niet openen:*&quot; of &quot;*Bestand of map bestaat niet*&quot; wanneer wordt geprobeerd updates voor ECE-tools, patches of andere wijzigingen in te voeren.

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

Onjuiste configuratie van uw `composer.json` bestand.

## Oplossing

Als een instelling ontbreekt in uw `composer.json` niet worden gekopieerd uit de Adobe Commerce Code Base. Het pakket en de update/patch kunnen niet worden toegepast omdat er geen bestanden worden gevonden.

Wijzig de extra sectie zodat deze overeenkomt met de onderstaande sectie en probeer de implementatie opnieuw uit te voeren.

```
"extra":{
  "magento-force": true,
  "magento-deploystrategy": "copy"
}
```

## Gerelateerde lezing

* [Upgrades en patches](https://devdocs.magento.com/guides/v2.3/cloud/project/project-upgrade-parent.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=update%20ece%20tools) in onze ontwikkelaarsdocumentatie.
