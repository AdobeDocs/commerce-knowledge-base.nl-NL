---
title: Veelvoorkomende fatale fouten en oplossingen in PHP
description: In dit artikel worden enkele veelvoorkomende snelle voorbeelden van PHP Fatal Error weergegeven die u kunt vinden wanneer u uw Adobe Commerce-logboeken doorzoekt en de oplossingen voor problemen die ze aangeven.
exl-id: 3e42d38f-97bc-4d38-8e36-23b1453f81d9
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Raadpleeg [&#x200B; aanpassen php.ini montages &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure/app/php-settings) artikel.

## Voorbeeld

*&#39;PHP Onherstelbare fout: Toegestane geheugengrootte van 792723456 bytes uitgeput&#39;* (Dat is slechts een voorbeeldbytegrootte.)

## Oplossing

Pas de `php.ini` -instellingen aan. Raadpleeg dit [&#x200B; aanpassen php.ini montages &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure/app/php-settings) artikel.

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

* [&#x200B; PHP montagesfouten &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/overview)
* [&#x200B; Vereiste PHP montages &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/prerequisites/php-settings)
* [&#x200B; herdis controle &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/cache/redis/redis-session#verify-redis-connection)
* [&#x200B; vormen Redis &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/cache/redis/config-redis)
* [&#x200B; PHP fout van de geheugengrens &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/overview)
* [&#x200B; Oplossingen aan gemeenschappelijke problemen - de grens van het Geheugen &#x200B;](https://developer.adobe.com/commerce/testing/guide/unit/command-line/#solutions-to-common-problems)
