---
title: Het controleren van langzame vragen en verwerkt MySQL
description: In dit artikel wordt gesproken over een aantal veelvoorkomende MySQL-problemen (trage query's, processen die te lang duren) die een nadelige invloed kunnen hebben op de site van een handelaar en de oplossingen die deze aangeeft.
exl-id: cae02e4f-d8cb-4074-abac-24ead22bdc07
feature: Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Het controleren van langzame vragen en verwerkt MySQL

In dit artikel wordt gesproken over een aantal veelvoorkomende MySQL-problemen (trage query&#39;s, processen die te lang duren) die een nadelige invloed kunnen hebben op de site van een handelaar en de oplossingen die deze aangeeft.

## MySQL &quot;slow query&quot; controleren

### Beschrijving

Als u een stroomstoring had die mogelijk door een overbelaste database werd veroorzaakt, kunt u met deze stappen het langzame querylogboek van uw database controleren.

### Vragen analyseren met MySQL-opdrachtregel (Adobe Commerce Cloud/on-premisse/Magento Open Source)

1. Meld u aan bij uw MySQL-opdrachtregel (Adobe Commerce on-premisse/Magento Open Source) of bij uw cloudserver via de opdrachtregel (Adobe Commerce on cloud Infrastructure).
1. Onderzoek het langzame vraaglogboek voor vragen langer dan 50 seconden:

   ```bash
   grep 'Query_time: [5-9][0-9]\|Query_time: [0-9][0-9][0-9]' /var/log/mysql/mysql-slow.log -A 3
   ```

1. Ga naar <https://www.unixtimestamp.com/> (of een vergelijkbare Unix-tijdstempelconverter) en voeg de tijdstempel in van wanneer de trage query is uitgevoerd.
1. Als de tijd met om het even welke plaatsuitbarsting correleert die u ervoer, kon het door een overbelaste gegevensbestand worden veroorzaakt. Controleer welke ladingen op dat ogenblik in het gegevensbestand waren. Voorbeelden van dergelijke ladingen zijn:

* Snijprocessen
* Verkeer (bots of mensen)
* Scripts importeren/exporteren
* dumpen maken


### Zoekopdrachten analyseren met [!DNL Percona Toolkit] (alleen Adobe Commerce Pro: Cloud-architectuur)

Als uw Adobe Commerce-project wordt geïmplementeerd op Pro-architectuur, kunt u query&#39;s analyseren met de [!DNL Percona Toolkit] .

1. Voer de opdracht `pt-query-digest --type=slowlog` uit op basis van MySQL langzame querylogs.
   * Om de plaats van de langzame vraaglogboeken te vinden, zie **[[!UICONTROL Log locations > Service Logs]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=nl-NL)** in onze ontwikkelaarsdocumentatie.
   * Zie de documentatie [[!DNL Percona Toolkit] > pt-query-digest &#x200B;](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) .
1. Gebaseerd op de gevonden kwesties, onderneem stappen om de vraag te bevestigen, zodat loopt het sneller.

## MySQL &quot;process list&quot; controleren

### Beschrijving

Dit zal helpen om te identificeren als de server MySQL levend is en dat er geen geplakte vragen zijn.

### Stappen

1. Meld u aan bij uw MySQL-opdrachtregel (Adobe Commerce on-premisse/Magento Open Source) of bij uw cloudserver via de opdrachtregel (Adobe Commerce on cloud Infrastructure).
1. Meld u met het onderstaande codeblok aan bij MySQL. Hierdoor wordt het aanmeldingsproces geautomatiseerd.

   ```MySQL
   `export DB_NAME=$(grep [\']db[\'] -A 20 app/etc/env.php | grep dbname | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_HOST=$(grep [\']db[\'] -A 20 app/etc/env.php | grep host | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export DB_USER=$(grep [\']db[\'] -A 20 app/etc/env.php | grep username | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_PWD=$(grep [\']db[\'] -A 20 app/etc/env.php | grep password | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/[']$//" | sed "s/['][,]//");    mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;`
   ```

1. Als u een fout terug krijgt of het meer dan 30 seconden vergt om te antwoorden, zou u Steun moeten contacteren om de server te controleren MySQL.
1. Bekijk de voorbeelduitvoer.

1. Hier volgt een voorbeeld van uitvoer:

   ```MySQL
   `$ mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;'    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | Id        | User          | Host               | db            | Command | Time | State          | Info                                                                                                 | Progress |    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | 123456789 | abcdefghijklm | 192.168.7.10:12345 | abcdefghijklm | Query   |    0 | Writing to net | SELECT `magento_versionscms_hierarchy_node`.*, `page_table`.`title` AS `page_title`, `page_table`.`i |    0.000 |    | 123456788 | abcdefghijklm | 192.168.7.10:12344 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456777 | abcdefghijklm | 192.168.7.10:12333 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456666 | abcdefghijklm | 192.168.5.8:12222  | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |`
   ```

1. Controleer de kolom &quot;Tijd&quot;voor om het even welke tijd groter dan 1800 seconden; dat wijst op een proces dat potentieel teveel tijd neemt om te voltooien. Noteer de status van de processen in de kolom &quot;Staat&quot;.
1. Herzie de vragen en misschien doden hen als zij worden gevonden niet om voor die tijdsduur te lopen. Het is mogelijk dat de lange lopende vragen kunnen worden verwacht.


## Gerelateerde lezing

* [&#x200B; MySQL toont Syntaxis van Processlist &#x200B;](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) in dev.mysql.com.
* [&#x200B; Syntaxis van de Kill MySQL &#x200B;](https://dev.mysql.com/doc/refman/8.0/en/kill.html) in dev.mysql.com.
* [&#x200B; Veiligheid, Prestaties, en de Behandeling van Gegevens &#x200B;](https://developer.adobe.com/commerce/php/best-practices/extensions/security/) in onze ontwikkelaarsdocumentatie.
* [&#x200B; Help MySQL &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql) in onze ontwikkelaarsdocumentatie.
