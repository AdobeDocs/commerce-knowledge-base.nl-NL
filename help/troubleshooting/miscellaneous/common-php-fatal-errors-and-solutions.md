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

*&#39;PHP Fatale fout: Maximale uitvoeringstijd van 60 seconden overschreden in...&#39;*

## Oplossing

U kunt de maximale uitvoeringstijd bijwerken door een aangepaste `max_execution_time` -waarde in te stellen in uw `php.ini` -bestand en deze opnieuw te implementeren.

Bijvoorbeeld:

`max_execution_time = 120`

Raadpleeg [ aanpassen php.ini montages ](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html) artikel.

## Voorbeeld

*&#39;PHP Onherstelbare fout: Toegestane geheugengrootte van 792723456 bytes uitgeput&#39;* (Dat is slechts een voorbeeldbytegrootte.)

## Oplossing

Pas de `php.ini` -instellingen aan. Raadpleeg dit [ aanpassen php.ini montages ](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html) artikel.

## Voorbeeld

*&#39;PHP Warning: Unknown: failed to open stream: No such file or directory&#39;*

## Oplossing

Verwijder de Windows-stijleinden niet uit het `php.ini` -bestand. In Windows worden regeleindes beëindigd met een combinatie van een regelterugloop (ASCII 0x0d of \r) en een nieuwe regel (\n), ook wel CR/LF genoemd.

## Voorbeeld

*&#39;PHP Fatal error: Uncaught PDOException: SQLSTATE\[HY000\] \[1040\] Too many connections in&#39;*

## Oplossing

De MySQL-omgeving heeft onvoldoende schijfruimte. Verstrek meer schijfruimte voor het milieu MySQL.

## Voorbeeld

*&#39;PHP Fatal error: Uncaught TypeError: Return value of Magento&#39;*

## Oplossing

Controleer de map `<root>/tmp` omdat deze waarschijnlijk vol is. Als de map vol is, geeft u meer ruimte op in de map. U kunt dit bijvoorbeeld doen door bestanden naar een andere map te verplaatsen of ze te verwijderen.

## Gerelateerde lezing

In onze documentatie voor ontwikkelaars:

* [ PHP montagesfouten ](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html)
* [ Vereiste PHP montages ](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html)
* [ herdis controle ](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify)
* [ vormen Redis ](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html)
* [ PHP fout van de geheugengrens ](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html#trouble-php-memory)
* [ Oplossingen aan gemeenschappelijke problemen - de grens van het Geheugen ](https://devdocs.magento.com/guides/v2.3/test/unit/unit_test_execution_cli.html#solutions-to-common-problems)
