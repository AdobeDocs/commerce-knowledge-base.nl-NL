---
title: Databasefouten met betrekking tot max_allowed_packet op Adobe Commerce
description: Dit artikel verstrekt een oplossing voor de fouten van de gegevensbestandverbinding in ` var/log/exception.log ` die kunnen voorkomen wanneer het invoeren van een groot aantal producten of het uitvoeren van een andere taak die de server dwingt om grotere pakketten te behandelen dan die in \ max_allowed_packet"worden geplaatst die groter is dan het gebrek, 16MB.
exl-id: e8932b72-91a3-43ea-800e-a6c7a5a17656
feature: Best Practices, Observability, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Databasefouten met betrekking tot max_allowed_packet op Adobe Commerce

Dit artikel biedt een oplossing voor databaseverbindingsfouten in het dialoogvenster `var/log/exception.log` dat kan voorkomen wanneer het invoeren van een groot aantal producten of het uitvoeren van een andere taak die de server dwingt grotere pakketten dan die binnen te behandelen `max_allowed_packet` dat groter is dan de standaard, 16 MB.

## Betrokken producten en versies

* Adobe Commerce op locatie, alle [ondersteunde versies](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Probleem

Wanneer een MySQL-client of de [mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html) server ontvangt een pakket dat groter is dan [max\_allowed\_packet](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet) bytes, geeft het een [ER\_NET\_PACKET\_TOO\_LARGE](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large) fout (die u kunt zien in de `exception.log`) en sluit de verbinding. Bij sommige clients kunt u ook een *Verbinding met MySQL-server verbroken tijdens query* fout als het communicatie pakket te groot is.

<u>Stappen om te reproduceren</u>

Dit probleem kan worden veroorzaakt door verschillende taken. Dit kan het proberen om een groot aantal producten in Adobe Commerce in te voeren of transactievragen omvatten die teveel gegevens terugsturen. Het resultaat is dat databaseverbindingsfouten optreden in `var/log/exception.log` en andere problemen, zoals producten die niet met succes worden geïmporteerd.

## Oorzaak

De standaardwaarde van 16MB voor MySQL `max_allowed_packets` deze instelling is niet groot genoeg voor uw behoeften.

## Oplossing

1. Identificeer vragen waar de individuele rijen huidige overschrijden `max_allowed_packet` limiet. Dergelijke vragen moeten worden herschreven om de hoeveelheid terug te geven gegevens te verminderen. Dit kan door een kleiner aantal kolommen in te hebben `SELECT` of het kiezen van een kleiner gegevenstype voor diverse kolommen als onderdeel van het tabelontwerp. Als u een New Relic-account hebt, gebruikt u de [New Relic APM-foutpagina](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors) en de [New Relic APM Databases-pagina](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time), en [New Relic Logs](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management) om de relevante vragen te zoeken.
1. Voor een snelle oplossing kunt u tijdelijk de opdracht `max_allowed_packet` te vergroten grootte wanneer u [een ticket verzenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), maar dit is naar goeddunken van het team van de Techniek van de Klant, aangezien te groot van een waarde replicatiefouten kan veroorzaken door netwerkcongestie te veroorzaken.
1. Als beste praktijken, zou u het volgende bevel in uw CLI voor sommige van uw grote gegevensbestandlijsten moeten in werking stellen:

   ```
   show table status like [table name to match]
   ```

   Evalueer de vragen die op deze lijsten lopen om te bepalen als u geadviseerde overschrijdt `max_allowed_packet` grootte van 16 MB. Volg het zelfde proces in stap één om de gegevens te verminderen die door dergelijke vragen worden teruggegeven.

## Gerelateerde lezing

* [Installatiehandleiding > MySQL](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/mysql.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=max%20allowed%2016%20MB) in onze ontwikkelaarsdocumentatie.
* [Uploaden database verliest verbinding met MySQL](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md) in onze kennisbasis voor ondersteuning.
* [Best practices voor databases voor Adobe Commerce op cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) in onze kennisbasis voor ondersteuning.
* [Aanbevolen procedures om prestatieproblemen met databases op te lossen](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) in onze kennisbasis voor ondersteuning.
