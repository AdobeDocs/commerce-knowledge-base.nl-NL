---
title: MySQL Server is weggegaan ​ fout op Adobe Commerce in cloud
description: In dit artikel wordt gesproken over de oplossing voor het probleem waarbij een foutbericht " *SQL server has away*" in het bestand ` cron.log` wordt weergegeven. Er kan een reeks symptomen optreden, waaronder problemen met het importeren van afbeeldingsbestanden of een mislukte implementatie.
exl-id: 14cb9a6d-6d25-4044-8f52-d65648c03431
feature: Cloud, Paas, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# MySQL Server is weggegaan &#x200B; fout op Adobe Commerce in cloud

In dit artikel wordt gesproken over de oplossing van het probleem waarvoor u een &quot; *SQL-server is verdwenen* &quot;- foutbericht in het dialoogvenster `cron.log` bestand. Er kan een reeks symptomen optreden, waaronder problemen met het importeren van afbeeldingsbestanden of een mislukte implementatie.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, alle [ondersteunde versies](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Probleem

Je ontvangt een &#39; *SQL-server is verdwenen* &quot;- foutbericht in het dialoogvenster `cron.log` bestand.

<u>Stappen om te reproduceren</u>

Importeer bestanden en activeer een implementatie.

<u>Verwacht resultaat</u>

Succesvolle implementatie.

<u>Werkelijk resultaat</u>

Foutbericht in `cron.log` :&quot; *SQLSTATE\[HY000\] \[2006\] MySQL-server is weg at/app/AAAAAAAAA/vendor/magento/zendframework1/library/Zend/Db/Adapter/Pdo/Abstract.php:144&quot;*

## Oorzaak

De `default_socket_timeout` waarde is ingesteld op te laag. Dit wordt veroorzaakt door de instelling `default_socket_timeout` . Als php om het even wat van het gegevensbestand MySQL binnen deze periode niet ontvangt, veronderstelt het het losgemaakt is en de fout veroorzaakt.

## Oplossing

1. De huidige time-outperiode controleren voor `default_socket_timeout` door in CLI te lopen:    ```    php -i |grep default_socket_timeout    ```
1. Afhankelijk van de tijdinstelling neemt de `default_socket_timeout` variabele aan de verwachte langst mogelijke runtime in de `/etc/platform/<project_name>/php.ini` bestand. Men stelt voor dat u tussen 10 en 15 minuten plaatst.
1. Leg het vast aan GIT en herimplementeer.

## Gerelateerde lezing

* [Uploaden database verliest verbinding met MySQL](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md)
* [Best practices voor databases voor Adobe Commerce op cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
* [Meest voorkomende databaseproblemen in Adobe Commerce met cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html)
