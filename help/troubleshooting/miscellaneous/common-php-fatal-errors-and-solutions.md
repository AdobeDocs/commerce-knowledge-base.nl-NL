---
title: Veelvoorkomende fatale fouten en oplossingen in PHP
description: In dit artikel worden enkele veelvoorkomende snelle voorbeelden van PHP Fatal Error weergegeven die u kunt vinden wanneer u uw Adobe Commerce-logboeken doorzoekt en de oplossingen voor problemen die ze aangeven.
exl-id: 3e42d38f-97bc-4d38-8e36-23b1453f81d9
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Veelvoorkomende fatale fouten en oplossingen in PHP

In dit artikel worden enkele veelvoorkomende snelle voorbeelden van PHP Fatal Error weergegeven die u kunt vinden wanneer u uw Adobe Commerce-logboeken doorzoekt en de oplossingen voor problemen die ze aangeven.

## Voorbeeld

*&#39;Fatale fout PHP: Maximale uitvoertijd van 60 seconden overschreden in...&#39;*

## Oplossing

U kunt de maximale uitvoeringstijd bijwerken door een aangepaste `max_execution_time` waarde in uw `php.ini` bestand en opnieuw implementeren.

Bijvoorbeeld:

`max_execution_time = 120`

Raadpleeg de [PHP.ini-instellingen aanpassen](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html) artikel.

## Voorbeeld

*&#39;PHP Fatal error: allowed memory size of 792723456 bytes expired&#39;* (Dit is slechts een voorbeeldgrootte.)

## Oplossing

Pas uw `php.ini` instellingen. Raadpleeg dit [PHP.ini-instellingen aanpassen](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html) artikel.

## Voorbeeld

*&#39;PHP Warning: Unknown: failed to open stream: No such file or directory&#39;*

## Oplossing

Zorg ervoor u niet de Vensters-stijl eindings in verwijdert `php.ini` bestand. In Windows worden regeleindes beëindigd met een combinatie van een regelterugloop (ASCII 0x0d of \r) en een nieuwe regel (\n), ook wel CR/LF genoemd.

## Voorbeeld

*&#39;Fatale PHP-fout: Niet-afgevangen PDOException: SQLSTATE\[HY000\] \[1040\] Te veel verbindingen in&#39;*

## Oplossing

De MySQL-omgeving heeft onvoldoende schijfruimte. Verstrek meer schijfruimte voor het milieu MySQL.

## Voorbeeld

*&#39;Fatale PHP-fout: Uncaught TypeError: Return value of Magento&#39;*

## Oplossing

Controleer de `<root>/tmp` map omdat deze waarschijnlijk vol is. Als de map vol is, geeft u meer ruimte op in de map. U kunt dit bijvoorbeeld doen door bestanden naar een andere map te verplaatsen of ze te verwijderen.

## Gerelateerde lezing

In onze documentatie voor ontwikkelaars:

* [Fouten in PHP-instellingen](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html)
* [Vereiste PHP-instellingen](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html)
* [Verificatie opnieuw uitschakelen](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify)
* [Redis configureren](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html)
* [Fout in PHP-geheugenlimiet](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html#trouble-php-memory)
* [Oplossingen voor algemene problemen - Geheugenlimiet](https://devdocs.magento.com/guides/v2.3/test/unit/unit_test_execution_cli.html#solutions-to-common-problems)
