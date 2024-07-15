---
title: 'Beheerde waarschuwingen voor Adobe Commerce: kritische waarschuwing van de Apdex'
description: Dit artikel bevat stappen voor het oplossen van problemen wanneer u een kritieke waarschuwing van Apdex voor Adobe Commerce in New Relic ontvangt. Met de Apdex-score wordt gemeten of gebruikers tevreden zijn met de responstijd van webtoepassingen en -services. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.
exl-id: b6d3d4f3-4abb-4285-8071-2b9fb06bfa3c
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: fbb24fb3c8b399f3b7e19c663eb4b168657498e6
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 0%

---

# Beheerde waarschuwingen voor Adobe Commerce: kritische waarschuwing van Apdex

Dit artikel bevat stappen voor het oplossen van problemen wanneer u een kritieke waarschuwing van Apdex voor Adobe Commerce in New Relic ontvangt. Met de Apdex-score wordt gemeten of gebruikers tevreden zijn met de responstijd van webtoepassingen en -services. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.

![ toepassing kritieke alarm ](assets/apdex-critical-magento-managed.png){width="500"}

## Betrokken producten en versies

* Adobe Commerce on cloud Infrastructure Pro-planarchitectuur
* Adobe Commerce on cloud Infrastructure Starter-planarchitectuur

## Probleem

U zult een beheerd alarm in New Relic ontvangen als u tot [ Beheerde alarm voor Adobe Commerce ](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) hebt ondertekend en één of meerdere waakzame drempels zijn overschreden. Deze waarschuwingen zijn door de Adobe ontwikkeld om handelaren een standaardset te bieden met inzichten van support en engineering.

<u> **doe!** </u>

* Abort om het even welke plaatsing die tot dit alarm wordt gepland wordt ontruimd.
* Zet uw site onmiddellijk in de onderhoudsmodus als uw site helemaal niet reageert of niet meer reageert. Voor stappen, verwijs naar [ Gids van de Installatie > laat of maakt onderhoudswijze ](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in onze ontwikkelingsdocumentatie toe onbruikbaar. Zorg ervoor om uw IP aan de Vrijgestelde IP adreslijst toe te voegen om ervoor te zorgen dat u nog tot uw plaats voor het oplossen van problemen kunt toegang hebben. Voor stappen, verwijs naar [ handhaaf de lijst van vrijgestelde IP adressen ](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) in onze ontwikkelaarsdocumentatie.

<u>**niet!**</u>

* Start aanvullende marketingcampagnes die extra pagina&#39;s naar uw site kunnen brengen.
* Voer indexen of extra kranen uit die extra belasting op de CPU of schijf kunnen veroorzaken.
* Voer belangrijke administratieve taken uit (zoals de Commerce Admin, gegevensimport/export).
* Wis uw cache.

Als u een kritische waarschuwing hebt ontvangen voordat u de oorzaak van de waarschuwing hebt opgelost, reageert uw site mogelijk niet meer als u nog geen probleem hebt met de site.

## Oplossing

Volg deze stappen om de oorzaak te identificeren en problemen op te lossen.

>[!WARNING]
>
>Omdat dit een kritiek alarm is, wordt het hoogst geadviseerd u **Stap 1** voltooit alvorens u probeert om de kwestie (Stap 2 vanaf) problemen op te lossen.

1. Controleer of er een Adobe Commerce-ondersteuningsticket bestaat. Voor stappen, verwijs naar [ Spoor uw steunkaartjes ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in onze basis van de steunkennis. De ondersteuning heeft mogelijk een New Relic-drempelwaardewaarschuwing ontvangen, een ticket gemaakt en aan het probleem gewerkt. Als er geen ticket bestaat, maakt u er een. Het ticket moet de volgende informatie bevatten:
   * Reden van contactpersoon: selecteer &quot;KRITISCHE waarschuwing van New Relic ontvangen&quot;.
   * Beschrijving van de signalering.
   * [ verbinding van het Ongeval van New Relic ](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dit is inbegrepen in uw [ Beheerde alarm voor Adobe Commerce ](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Om de bron van het probleem te identificeren, gebruik {de pagina van de Transactie van 0} New Relic APM ](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) om transacties met prestatieskwesties te identificeren:[
   * Transacties sorteren door oplopende Apdex-scores. [ Apdex ](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) verwijst naar gebruikerstevredenheid aan de reactietijd van uw Webtoepassingen en de diensten. Een lage Apdex-score kan een knelpunt aangeven (een transactie met een hogere responstijd). Meestal is dit de database, Redis of PHP. Voor stappen, verwijs naar de transacties van de Mening van New Relic [ met de hoogste ontevredenheid van de Index ](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction/#dissatisfaction).
   * De transacties van de soort door hoogste productie, de langzaamste gemiddelde reactietijd, het meest tijdrovend, en andere drempels. Voor stappen, verwijs naar New Relic [ vind specifieke prestatiesproblemen ](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Als u het probleem nog steeds niet kunt identificeren, gebruikt u de pagina Infrastructuur van New Relic APM.
1. De pagina van de Infrastructuur van New Relic APM van het gebruik ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) om middel intensieve processen te identificeren. [ Voor stappen, verwijs naar de pagina van de Gastheren van de Infrastructuur van New Relic [ controle > het lusje van Processen ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Als de diensten zoals Redis of MySQL de hoogste bron van geheugenconsumptie zijn, probeer het volgende:
   * Controleer of u de meest recente versie hebt. In nieuwere versies kunnen soms geheugenlekken worden gecorrigeerd. Als u niet over de nieuwste versie beschikt, kunt u een upgrade uitvoeren. Voor stappen, verwijs naar [ Wolk voor Adobe Commerce > de Diensten > de Diensten van de Verandering ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) in onze ontwikkelaarsdocumentatie.
   * Controleer of er MySQL-problemen zijn, zoals query&#39;s die lang worden uitgevoerd, primaire sleutels die niet zijn gedefinieerd en dubbele indexen. Voor stappen, verwijs naar [ Veelvoorkomende gegevensbestandKwesties in Adobe Commerce op wolkeninfrastructuur ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) in onze ontwikkelaarsdocumentatie.
   * Controleren op PHP-problemen. Herzie lopende processen door `ps aufx` in CLI/Terminal in werking te stellen. In de eindoutput zult u cron banen en processen zien die momenteel worden uitgevoerd. Controleer de uitvoer op de uitvoeringstijd van het proces. Als er een kruin met een lange uitvoeringstijd is, kan de kruin hangen. Voor het oplossen van problemenstappen, verwijs naar [ Trage prestaties, langzame en lange lopende kronnen ](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) en [ baan van het Gewas die in &quot;lopende&quot;status ](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) in onze steunkennisbasis wordt geplakt.

1. Zodra de bron is geïdentificeerd, bevindt SSH zich in het milieu om verder te onderzoeken. Voor stappen, verwijs naar [ Wolk voor Adobe Commerce > Technologieën en vereisten > SSH in uw milieu ](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) in onze ontwikkelaarsdocumentatie.
1. Als u nog worstelt om de bron te identificeren, herzie recente tendensen om kwesties met recente codeplaatsingen of configuratieveranderingen (bijvoorbeeld, nieuwe klantengroepen en grote veranderingen in de catalogus) te identificeren. U wordt aangeraden de afgelopen zeven dagen van activiteit te controleren op correlaties in codeimplementaties of -wijzigingen.
1. Als u niet binnen een redelijke termijn een oplossing kunt vinden, verzoek om een vergrote of plaats in onderhoudswijze als u nog niet hebt gedaan. Voor stappen, verwijs naar [ hoe te om tijdelijk te verzoeken resize ](/help/how-to/general/how-to-request-temporary-magento-upsize.md) in onze basis van de steunkennis, en [ Gids van de Installatie > laat of maakt onderhoudswijze ](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in onze ontwikkelaarsdocumentatie toe onbruikbaar.
1. Als de upsize de plaats aan normale verrichtingen terugkeert, denk na om permanent te verzoeken (uw Team van de Rekening van de Adobe), of probeer om het probleem in uw Dedicated Staging te reproduceren door een ladingstest in werking te stellen en vragen te optimaliseren, of code die druk op de diensten vermindert. Verwijs naar [ Wolk voor Adobe Commerce > de Plaatsing van de Test > het Testen van de Lading en stress ](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) in onze ontwikkelaarsdocumentatie.
