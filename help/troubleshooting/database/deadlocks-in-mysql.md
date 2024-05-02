---
title: Deadlocks in MySQL
description: In dit artikel wordt gesproken over blokkeringen in MySQL om hen te helpen identificeren en op te lossen als ze een site neerzetten, vastgelopen database-import of andere Adobe Commerce-problemen veroorzaken.
exl-id: 529d1c0b-77f3-4604-9878-e7ea2c9c3640
feature: Best Practices, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Deadlocks in MySQL

In dit artikel wordt gesproken over blokkeringen in MySQL om hen te helpen identificeren en op te lossen als ze een site neerzetten, vastgelopen database-import of andere Adobe Commerce-problemen veroorzaken.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.2.x en 2.3.x
* Adobe Commerce op cloudinfrastructuur 2.2.x en 2.3.x

## Probleem

Deadlocks in MySQL komen voor wanneer twee of meer transacties wederzijds houden en verzoeken om sloten. De aanwezige vertragingen wijzen niet altijd op een kwestie maar zijn vaak een symptoom van een andere kwestie MySQL of Adobe Commerce die is voorgekomen.

Vaak zullen de toepassing, de plaatsing, of Logboeken MySQL het *&quot;impasse&quot;* fout of fout *&quot;Deadlock found when try to get lock; try restarted transaction.&quot;*

## Oorzaak

Deadlocks kunnen veelvoudige oorzaken hebben, maar het gemeenschappelijkst is als u om het even welke interactie (website/processen/kanonnen banen/andere gebruikers/MySQL onderhoud/MySQL de invoer) terwijl het uitvoeren van vragen DML/DDL tezelfdertijd uitvoert.

Als voorbeeld, is het beste praktijken om een geplakt MySQL gegevensbestandinvoer te vermijden door uw plaats eerst op onderhoudswijze te zetten vermijden hebbend SQL- verzoeken aan het gegevensbestand die importeert van de importeerbaarheid en een geplakt gegevensbestand kon veroorzaken.

## Oplossing

1. Controleer uw toepassing, plaatsing, of Logboeken MySQL voor vastzettingsfouten:
   * [Adobe Commerce- en Magento Open Source-loglocaties](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/enable-logging.html)
   * [Adobe Commerce op locatie voor logbestanden met cloud-infrastructuur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)
1. Controleer uw MySQL proceslijst voor het runnen van processen met het bevel `mysql -e 'show full processlist';`
1. Controleer of MySQL-slave is ingeschakeld in Adobe Commerce op cloudinfrastructuur. Raadpleeg dit artikel: [Variabelen implementeren (MYSQL\_USE\_SLAVE\_CONNECTION)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection).
1. Afhankelijk van de fouten kan de oplossing zich voorstellen, of u kunt uw nuttige logboekinformatie moeten omvatten als u een [Support-ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Gerelateerde lezing

* [Hoe te om Deadlocks te minimaliseren en te behandelen](https://dev.mysql.com/doc/refman/5.7/en/innodb-deadlocks-handling.html)
* [Indexeroptimalisatie - Indexer Table Switching](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/)
* [Bulkbewerkingen - Berichten consumeren](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

>[!NOTE]
>
>We zijn ons ervan bewust dat dit artikel wellicht nog steeds standaardsoftwaretermen bevat die sommigen racistisch, seksistisch of onderdrukkend vinden en die de lezer kunnen doen voelen gekwetst, getraumatiseerd of onwelkom. Adobe werkt eraan deze termen te verwijderen uit onze code, documentatie en gebruikerservaring.
