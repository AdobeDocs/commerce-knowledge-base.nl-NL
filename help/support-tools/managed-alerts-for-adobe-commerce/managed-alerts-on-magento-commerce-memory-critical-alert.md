---
title: 'Beheerde waarschuwingen voor Adobe Commerce: waarschuwing voor geheugenproblemen'
description: Dit artikel bevat stappen voor het oplossen van problemen wanneer u een belangrijke waarschuwing voor Adobe Commerce in New Relic ontvangt. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.
exl-id: feed7998-c50b-4cbf-a92d-cbfc65745a1c
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 0%

---

# Beheerde waarschuwingen voor Adobe Commerce: waarschuwing voor geheugenproblemen

Dit artikel bevat stappen voor het oplossen van problemen wanneer u een belangrijke waarschuwing voor Adobe Commerce in New Relic ontvangt. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.

![ schijf kritiek alarm ](assets/memory-critical-magento-managed.png){width="500"}

## Betrokken producten en versies

Alle versies van Adobe Commerce op cloudinfrastructuur Pro plannen.

## Probleem

U zult een beheerd alarm in New Relic ontvangen als u tot [ Beheerde alarm voor Adobe Commerce ](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) hebt ondertekend en één of meerdere waakzame drempels zijn overschreden. Deze waarschuwingen zijn door de Adobe ontwikkeld om klanten een standaardset te bieden met inzichten van support en engineering.

<u> **doe!** </u>

* Alle geplande implementaties afbreken totdat deze waarschuwing wordt gewist
* Zet uw site onmiddellijk in de onderhoudsmodus als uw site helemaal niet reageert of niet meer reageert. Voor stappen, zie [ Gids van de Installatie > toelaten of onderhoudswijze ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in onze ontwikkelaarsdocumentatie onbruikbaar maken. Zorg ervoor om uw IP aan de Vrijgestelde IP adreslijst toe te voegen om ervoor te zorgen dat u nog tot uw plaats voor het oplossen van problemen kunt toegang hebben. Voor stappen, zie [ de lijst van vrijgestelde IP adressen ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt) in onze ontwikkelaarsdocumentatie handhaven.

<u>**niet!**</u>

* Start aanvullende marketingcampagnes die extra pagina&#39;s naar uw site kunnen brengen.
* Voer indexen of extra kranen uit die extra belasting op de CPU of schijf kunnen veroorzaken.
* Voer belangrijke administratieve taken uit (bijvoorbeeld Commerce Admin, gegevensimport/export).
* Wis uw cache.

Uw site reageert mogelijk niet meer (als er nog geen site-uitval optreedt) als u een van de acties &quot;Niet uitvoeren&quot; uitvoert voordat u de oorzaak van de waarschuwing hebt onderzocht en opgelost.

## Oplossing

Volg deze stappen om de oorzaak te identificeren en problemen op te lossen.

>[!WARNING]
>
>Omdat dit een kritiek alarm is, wordt het hoogst geadviseerd u **Stap 1** voltooit alvorens u probeert om de kwestie (Stap 2 vanaf) problemen op te lossen.

1. Controleer of er een Adobe Commerce-ondersteuningsticket bestaat. Voor stappen, zie [ Spoor uw steunkaartjes ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in onze basis van de steunkennis. De ondersteuning heeft mogelijk al een New Relic-drempelwaardewaarschuwing ontvangen, een ticket gemaakt en aan het probleem gewerkt. Als er geen ticket bestaat, maakt u er een. Het ticket moet de volgende informatie bevatten:
   * Reden van contactpersoon: selecteer &quot;KRITIEKE New Relic-waarschuwing ontvangen&quot;
   * Beschrijving van de signalering
   * [ verbinding van het Ongeval van New Relic ](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dit is inbegrepen in uw [ Beheerde alarm voor Adobe Commerce ](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).

1. De pagina van de Infrastructuur van New Relic APM van het gebruik ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) om hoogste geheugen intensieve processen te identificeren. [ Voor stappen, verwijs naar de pagina van de Gastheren van de Infrastructuur van New Relic [ > het lusje van Processen ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes):
   * Als services zoals Redis, MySQL of PHP de belangrijkste bronnen van geheugenverbruik zijn, kunt u het volgende proberen:
1. Controleer of u de nieuwste versies hebt. In nieuwere versies kunnen soms geheugenlekken worden gecorrigeerd. Als u niet over de nieuwste versie beschikt, kunt u een upgrade uitvoeren. Voor stappen, verwijs naar [ Adobe Commerce op wolkeninfrastructuur > de Diensten > de Diensten van de Verandering ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) in onze ontwikkelaarsdocumentatie.
1. Als het probleem met de service geen versiegerelateerd probleem is, probeert u het volgende:
1. **MySQL**: Controle voor kwesties zoals lange lopende vragen, Primaire sleutels bepaald niet, en dubbele indexen. Voor stappen, verwijs naar [ Veelvoorkomende gegevensbestandKwesties in Adobe Commerce op wolkeninfrastructuur ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) in onze basis van steunkennis.
1. **Redis**: Als Redis een hoogste bron van geheugenconsumptie is, [ voorlegt een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
1. **PHP**: Als PHP een hoogste bron van geheugenconsumptie is, herzie lopende processen door `ps aufx` in CLI/Terminal in werking te stellen. In de eindoutput zult u cron banen en processen zien die momenteel worden uitgevoerd. Controleer de uitvoer op de uitvoeringstijd van het proces. Als er een kruin met een lange uitvoeringstijd is, kan de kruin hangen. Voor het oplossen van problemenstappen, zie [ Trage prestaties, langzame en lange lopende kronnen ](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) en [ baan van het Gewas geplakt in &quot;lopende&quot;status ](https://support.magento.com/hc/en-us/articles/360033099451) in onze basis van steunkennis.
1. Als u nog worstelt om de bron van het probleem te identificeren, gebruik [ pagina van de Transactie van New Relic APM ](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) om transacties met prestatieskwesties te identificeren:
   * Transacties sorteren door oplopende Apdex-scores. [ Apdex ](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) verwijst naar gebruikerstevredenheid aan de reactietijd van uw Webtoepassingen en de diensten. A [ lage score van de Index ](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) kan op een knelpunt (een transactie met een hogere reactietijd) wijzen. Meestal is dit de database, Redis of PHP. Voor stappen, verwijs naar de transacties van de Mening van New Relic [ met de hoogste ontevredenheid van de Index ](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * De transacties van de soort door hoogste productie, de langzaamste gemiddelde reactietijd, het meest tijdrovend, en andere drempels. Voor stappen, verwijs naar New Relic [ vind specifieke prestatiesproblemen ](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Als u het probleem nog steeds niet kunt identificeren, gebruikt u de pagina Infrastructuur van New Relic APM.
1. Als u niet de oorzaak van verhoogde geheugenconsumptie kunt identificeren, herzie recente tendensen om kwesties met recente codeplaatsingen of configuratieveranderingen (bijvoorbeeld, nieuwe klantengroepen en grote veranderingen in de catalogus) te identificeren. U wordt aangeraden de afgelopen 7 dagen van activiteit te controleren op correlaties in codeimplementaties of -wijzigingen.
1. Als de bovenstaande methoden u niet helpen de oorzaak en/of oplossing binnen een redelijke tijd te vinden, kunt u een upgrade aanvragen of de site in de onderhoudsmodus plaatsen als u dat nog niet hebt gedaan. Voor stappen, zie [ hoe te om tijdelijk te verzoeken resize ](/help/how-to/general/how-to-request-temporary-magento-upsize.md) in onze basis van de steunkennis, en [ Gids van de Installatie > laat of maakt onderhoudswijze ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in onze ontwikkelaarsdocumentatie toe onbruikbaar.
1. Als de upsize de plaats aan normale verrichtingen terugkeert, denk na om permanent te verzoeken (uw Team van de Rekening van de Adobe), of probeer om het probleem in uw Dedicated Staging te reproduceren door een ladingstest in werking te stellen en vragen te optimaliseren, of code die druk op de diensten vermindert. Zie [ Adobe Commerce op wolkeninfrastructuur > de Plaatsing van de Test > het Testen van de Lading en stress ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) in onze ontwikkelaarsdocumentatie.
