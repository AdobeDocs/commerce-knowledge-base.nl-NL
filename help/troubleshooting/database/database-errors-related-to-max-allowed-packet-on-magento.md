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

Dit artikel biedt een oplossing voor databaseverbindingsfouten in de `var/log/exception.log` die kunnen optreden wanneer u een groot aantal producten importeert of een andere taak uitvoert die de server dwingt grotere pakketten af te handelen dan in `max_allowed_packet` is ingesteld, die groter is dan de standaardwaarde (16 MB).

## Betrokken producten en versies

* Adobe Commerce op-gebouw, alle [ gesteunde versies ](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Probleem

Wanneer een cliënt MySQL of de [ mysqld ](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html) server een pakket groter dan [ max\_allowed\_packet ](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet) bytes ontvangt, geeft het een [ ER\_NET\_PACKET\_TOO\_LARGE ](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large) fout uit (die in `exception.log`) kan worden gezien en sluit de verbinding. Met sommige cliënten, kunt u a *Verloren verbinding aan server MySQL tijdens vraag* fout ook krijgen als het communicatie pakket te groot is.

<u> Stappen om te reproduceren </u>

Dit probleem kan worden veroorzaakt door verschillende taken. Dit kan het proberen om een groot aantal producten in Adobe Commerce in te voeren of transactievragen omvatten die teveel gegevens terugsturen. Het resultaat is een fout in de databaseverbinding in `var/log/exception.log` en andere problemen, zoals producten die niet correct zijn geïmporteerd.

## Oorzaak

De standaardwaarde van 16 MB voor de instelling MySQL `max_allowed_packets` is niet groot genoeg voor uw behoeften.

## Oplossing

1. Identificeer vragen waar de individuele rijen de huidige `max_allowed_packet` grens overschrijden. Dergelijke vragen moeten worden herschreven om de hoeveelheid terug te geven gegevens te verminderen. Dit kan door een kleiner aantal kolommen in de `SELECT` verklaring te hebben of een kleiner gegevenstype voor diverse kolommen als deel van het lijstontwerp te kiezen. Als u een rekening van New Relic hebt, gebruik de [ pagina van de Fouten van New Relic APM ](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors) en de [ pagina van de Gegevensbestanden van New Relic APM ](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time), en [ Logs van New Relic ](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management) om naar de relevante vragen te zoeken.
1. Voor snelle sanering, kunt u tijdelijk verzoeken om de `max_allowed_packet` grootte om worden verhoogd wanneer u [ een kaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voorlegt, maar dit is bij de discretie van het team van de Techniek van de Klant, aangezien te groot van een waarde replicatiefouten kan veroorzaken door netwerkcongestie te veroorzaken.
1. Als beste praktijken, zou u het volgende bevel in uw CLI voor sommige van uw grote gegevensbestandlijsten moeten in werking stellen:

   ```
   show table status like [table name to match]
   ```

   Evalueer de vragen die op deze lijsten lopen om te bepalen als u de geadviseerde `max_allowed_packet` grootte van 16MB overschrijdt. Volg het zelfde proces in stap één om de gegevens te verminderen die door dergelijke vragen worden teruggegeven.

## Gerelateerde lezing

* [ Gids van de Installatie > MySQL ](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/mysql.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=max%20allowed%2016%20MB) in onze ontwikkelaarsdocumentatie.
* [ uploadt het Gegevensbestand verliest verbinding aan MySQL ](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md) in onze basis van de steunkennis.
* [ beste praktijken van het Gegevensbestand voor Adobe Commerce op wolkeninfrastructuur ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) in onze basis van steunkennis.
* [ Beste praktijken om de kwesties van gegevensbestandprestaties ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) in onze basis van de steunkennis op te lossen.
