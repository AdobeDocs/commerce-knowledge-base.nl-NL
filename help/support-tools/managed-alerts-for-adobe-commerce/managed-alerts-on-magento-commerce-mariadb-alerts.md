---
title: "Beheerde waarschuwingen over Adobe Commerce: MariaDB-waarschuwingen"
description: 'Dit artikel bevat stappen voor het oplossen van problemen wanneer u MariaDB-waarschuwingen voor Adobe Commerce in New Relic ontvangt. Het MariaDB- alarm controleert hoge vraaglading evenals bovenmatige vragen van de Manipulatie van Gegevens van de Taal (DML). Beide kunnen leiden tot een verminderde gebruikerservaring of zelfs downtime. U kunt vier soorten waarschuwingen ontvangen:'
exl-id: 707e20e0-faba-4bcd-884c-b54568787442
feature: Cache, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Beheerde waarschuwingen over Adobe Commerce: MariaDB-waarschuwingen

Dit artikel bevat stappen voor het oplossen van problemen wanneer u MariaDB-waarschuwingen voor Adobe Commerce in New Relic ontvangt. Het MariaDB- alarm controleert hoge vraaglading evenals bovenmatige vragen van de Manipulatie van Gegevens van de Taal (DML). Beide kunnen leiden tot een verminderde gebruikerservaring of zelfs downtime. U kunt vier soorten waarschuwingen ontvangen:

* Waarschuwing DML-query&#39;s
* DML vraagt kritiek

## **Betrokken producten en versies**

Adobe Commerce on cloud Infrastructure Pro-planarchitectuur

## Probleem

Je ontvangt een beheerde waarschuwing in New Relic als je je hebt aangemeld bij [Beheerde waarschuwingen voor Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) en een of meer alarmdrempels zijn overschreden. Deze waarschuwingen zijn door de Adobe ontwikkeld om klanten een standaardset te bieden met inzichten van support en engineering.

**Doe het!**

* Abort om het even welke plaatsing die tot dit alarm wordt gepland wordt ontruimd.
* Zet uw site onmiddellijk in de onderhoudsmodus als uw site helemaal niet reageert of niet meer reageert. Zie voor stappen [Installatiegids > Onderhoudsmodus in- of uitschakelen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in onze ontwikkelaarsdocumentatie. Zorg ervoor om uw IP aan de Vrijgestelde IP adreslijst toe te voegen om ervoor te zorgen dat u nog tot uw plaats voor het oplossen van problemen kunt toegang hebben. Raadpleeg voor stappen [Handhaaf de lijst van vrijgestelde IP adressen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt).
* Beëindig alle scripts, zoals import die de oorzaak van de waarschuwing kunnen zijn als de prestaties van de site worden beïnvloed.

**Niet doen!**

* Voer indexeerders of extra kranen uit die extra druk op MariaDB kunnen veroorzaken.
* Voer belangrijke administratieve taken uit (bijvoorbeeld Commerce Admin, gegevensimport/export).
* Wis uw cache.

## Oplossing

**DML-query&#39;s (query&#39;s die de database wijzigen met UPDATE, INSERT en DELETE)**

Als u een Kritieke waakzame begin van Vragen DML bij stap ontvangt. Als u een DML- Vragen waarschuwingsalarm begint bij stap twee.

1. Controleer of er een Adobe Commerce-ondersteuningsticket bestaat. Raadpleeg onze kennisbasis voor stappen [Volg uw ondersteuningstickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets). De ondersteuning heeft mogelijk een New Relic-drempelwaardewaarschuwing ontvangen, een ticket gemaakt en aan het probleem gewerkt. Als er geen ticket bestaat, maakt u er een. Het ticket moet de volgende informatie bevatten:
1. Reden van contactpersoon: selecteer &quot;New Relic MariaDB-waarschuwing ontvangen&quot;.
1. Beschrijving van de signalering.
1. [New Relic Incident Link](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dit is inbegrepen in uw [Beheerde waarschuwingen voor Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Om de bron van de kwestie te identificeren, probeer om de vragen te identificeren DML:
1. Controleer uw databasebewerkingen met behulp van stappen uit New Relic [APM UI Pages > Monitoring > Databases page](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time) .
1. Sorteren op AANTAL AANROEPEN en vervolgens OP BEWERKING. De verrichtingen van het TUSSENVOEGSEL van het overzicht, DELETE, en van de UPDATE.
1. Kies voor een hoge AVG.
1. Klik door om de bezoekers van de gegevensbestandverrichting te vinden. Dit zal transacties identificeren die die vraag tegen tijd gebruiken.
1. Zoek uit of code optimaliseert, of operationele optimalisaties:
1. Codeoptimalisaties: kijk hoe u query&#39;s kunt optimaliseren met bulkinvoegingen / updates, het indexgebruik kunt minimaliseren of code kunt vertragen.
1. Operationele optimalisaties: Verplaats de hulpmiddelintensieve gegevenswijzigingen aan lagere verkeerstijden.
1. Aanvullende optimalisaties: zorg dat u de nieuwste versie van ECE-Tools gebruikt. Raadpleeg voor stappen [Cloud voor Adobe Commerce > Versie van bureaubladgereedschappen bijwerken](https://devdocs.magento.com/cloud/project/ece-tools-update.html) in onze ontwikkelaarsdocumentatie.

## Verwante lezing

* Voor onderzoek naar andere veelvoorkomende MariaDB-problemen raadpleegt u [Meest voorkomende databaseproblemen voor Adobe Commerce op cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html).
* Raadpleeg voor informatie over beste praktijken in de onderzoeksdatabase [Best practices voor databases voor Adobe Commerce op cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html).
