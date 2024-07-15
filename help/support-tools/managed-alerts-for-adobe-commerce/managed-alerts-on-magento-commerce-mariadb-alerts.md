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

## **beïnvloede producten en versies**

Adobe Commerce on cloud Infrastructure Pro-planarchitectuur

## Probleem

U zult een beheerd alarm in New Relic ontvangen als u tot [ Beheerde alarm voor Adobe Commerce ](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) hebt ondertekend en één of meerdere waakzame drempels zijn overschreden. Deze waarschuwingen zijn door de Adobe ontwikkeld om klanten een standaardset te bieden met inzichten van support en engineering.

**doe!**

* Abort om het even welke plaatsing die tot dit alarm wordt gepland wordt ontruimd.
* Zet uw site onmiddellijk in de onderhoudsmodus als uw site helemaal niet reageert of niet meer reageert. Voor stappen verwijzen naar [ Gids van de Installatie > laat of maakt onderhoudswijze ](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in onze ontwikkelaarsdocumentatie toe onbruikbaar. Zorg ervoor om uw IP aan de Vrijgestelde IP adreslijst toe te voegen om ervoor te zorgen dat u nog tot uw plaats voor het oplossen van problemen kunt toegang hebben. Voor stappen, verwijs naar [ handhaaf de lijst van vrijgestelde IP adressen ](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt).
* Beëindig alle scripts, zoals import die de oorzaak van de waarschuwing kunnen zijn als de prestaties van de site worden beïnvloed.

**niet!**

* Voer indexeerders of extra kranen uit die extra druk op MariaDB kunnen veroorzaken.
* Voer belangrijke administratieve taken uit (bijvoorbeeld Commerce Admin, gegevensimport/export).
* Wis uw cache.

## Oplossing

**Vragen DML (vragen die het gegevensbestand gebruikend UPDATE, INSERT, en DELETE) wijzigen**

Als u een Kritieke waakzame begin van Vragen DML bij stap ontvangt. Als u een DML- Vragen waarschuwingsalarm begint bij stap twee.

1. Controleer of er een Adobe Commerce-ondersteuningsticket bestaat. Voor stappen, verwijs naar onze kennisbasis [ Spoor uw steunkaartjes ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets). De ondersteuning heeft mogelijk een New Relic-drempelwaardewaarschuwing ontvangen, een ticket gemaakt en aan het probleem gewerkt. Als er geen ticket bestaat, maakt u er een. Het ticket moet de volgende informatie bevatten:
1. Reden van contactpersoon: selecteer &quot;New Relic MariaDB-waarschuwing ontvangen&quot;.
1. Beschrijving van de signalering.
1. [ verbinding van het Ongeval van New Relic ](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dit is inbegrepen in uw [ Beheerde alarm voor Adobe Commerce ](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Om de bron van de kwestie te identificeren, probeer om de vragen te identificeren DML:
1. Herzie uw gegevensbestandverrichtingen door stappen van de Pagina&#39;s van APM van New Relic [ te gebruiken UI > Controle > de pagina van Gegevensbestanden ](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time).
1. Sorteren op AANTAL AANROEPEN en vervolgens OP BEWERKING. De verrichtingen van het TUSSENVOEGSEL van het overzicht, DELETE, en van de UPDATE.
1. Kies voor een hoge AVG.
1. Klik door om de bezoekers van de gegevensbestandverrichting te vinden. Dit zal transacties identificeren die die vraag tegen tijd gebruiken.
1. Zoek uit of code optimaliseert, of operationele optimalisaties:
1. Codeoptimalisaties: kijk hoe u query&#39;s kunt optimaliseren met bulkinvoegingen / updates, het indexgebruik kunt minimaliseren of code kunt vertragen.
1. Operationele optimalisaties: Verplaats de hulpmiddelintensieve gegevenswijzigingen aan lagere verkeerstijden.
1. Aanvullende optimalisaties: zorg dat u de nieuwste versie van ECE-Tools gebruikt. Voor stappen, verwijs naar [ Wolk voor Adobe Commerce > update knoop-hulpmiddelen versie ](https://devdocs.magento.com/cloud/project/ece-tools-update.html) in onze ontwikkelaarsdocumentatie.

## Verwante lezing

* Om andere gemeenschappelijke kwesties te onderzoeken MariaDB, verwijs naar [ gemeenschappelijkste gegevensbestandkwesties voor Adobe Commerce op wolkeninfrastructuur ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html).
* Om gegevensbestand beste praktijken te onderzoeken, verwijs naar [ beste praktijken van het Gegevensbestand voor Adobe Commerce op wolkeninfrastructuur ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html).
