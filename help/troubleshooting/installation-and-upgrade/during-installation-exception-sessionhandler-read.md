---
title: Tijdens de installatie, uitzondering SessionHandler::read()
description: Dit artikel bevat een oplossing voor een uitzondering **SessionHandler::read()**-fout tijdens de installatie van Adobe Commerce.
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# Tijdens de installatie, uitzondering SessionHandler::read()

Dit artikel verstrekt een moeilijke situatie voor een uitzondering **SessionHandler::read ()** fout tijdens de installatie van Adobe Commerce.

## Probleem

Bij de laatste stap van de installatie van Adobe Commerce wordt de volgende uitzondering weergegeven:

```temrinal
exception 'Exception' with message 'Warning: SessionHandler::read():
open(..) failed: No such file or directory (2) ../magento2/lib/internal/Magento/Framework/Session/SaveHandler.php on line 74'
in ../magento2/lib/internal/Magento/Framework/App/ErrorHandler.php:67
```

>[!NOTE]
>
>Deze fout treedt alleen op in codeversies ouder dan 28 september 2015. Als u code van 29 september of later installeert, zou deze fout niet moeten voorkomen. Voor meer informatie over configuratieopties voor Redis, zie [ Redis ](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/cache/redis/config-redis) in onze ontwikkelaarsdocumentatie vormen. Voor meer informatie over het specificeren van Redis gebruikend het bevel-lijn installatieprogramma, zie het [ installatieonderwerp ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/advanced) of het [ onderwerp van de plaatsingsconfiguratie ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/tutorials/deployment) in onze ontwikkelaarsdocumentatie.

## Oorzaak

Dit gebeurt wanneer uw `session.save_handler` PHP-parameter is ingesteld op een andere sessieopslag dan `files` (bijvoorbeeld `redis` , `memcached` , enzovoort). Dit is een bekend probleem dat we proberen op te lossen.

## Oplossingen:

* Upgrade uw Adobe Commerce-code. Verwijs naar [ Gids van de Installatie > werk de software van Adobe Commerce ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/tutorials/uninstall) in onze ontwikkelaarsdocumentatie bij.
* Gebruik de volgende tijdelijke oplossing met bestaande code:

## Zoeken `php.ini` {#locate-php-ini}

Zoek `php.ini` door de volgende opdracht in te voeren:

```php
php -i | grep "Loaded Configuration File"
```

Hier volgen typische locaties:

* Ubuntu: `/etc/php5/cli/php.ini`
* CentOS: `/etc/php.ini`

## Workaround {#workaround}

1. Als gebruiker met `root` rechten, opent u `php.ini` in een teksteditor.
1. Zoeken `session.save_handler`
1. Stel de optie in op een van de volgende manieren:
   * Opmerkingen toevoegen:

     ```php
     ;session.save_path = <path>
     ```

   * U stelt als volgt het pad in op een bestandssysteem:

     ```php
     session.save_handler = files
     ```
