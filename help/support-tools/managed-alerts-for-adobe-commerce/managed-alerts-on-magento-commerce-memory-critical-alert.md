---
title: 'Beheerde waarschuwingen over Adobe Commerce: waarschuwing voor essentieel geheugen'
description: Dit artikel bevat stappen voor het oplossen van problemen wanneer u een belangrijke waarschuwing voor Adobe Commerce in New Relic ontvangt. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.
exl-id: feed7998-c50b-4cbf-a92d-cbfc65745a1c
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 468ad1c47da3c299b8028726e79e25a4aa9489ea
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 0%

---

# Beheerde waarschuwingen voor Adobe Commerce: waarschuwing voor geheugenproblemen

Dit artikel bevat stappen voor het oplossen van problemen wanneer u een belangrijke waarschuwing voor Adobe Commerce in New Relic ontvangt. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.

![kritieke schijf-waarschuwing](assets/memory-critical-magento-managed.png){width="500"}

## Betrokken producten en versies

Alle versies van Adobe Commerce op cloudinfrastructuur Pro plannen.

## Probleem

Je ontvangt een beheerde waarschuwing in New Relic als je je hebt aangemeld bij [Beheerde waarschuwingen voor Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) en een of meer alarmdrempels zijn overschreden. Deze waarschuwingen zijn door de Adobe ontwikkeld om klanten een standaardset te bieden met inzichten van support en engineering.

<u> **Doe het!** </u>

* Alle geplande implementaties afbreken totdat deze waarschuwing wordt gewist
* Zet uw site onmiddellijk in de onderhoudsmodus als uw site helemaal niet reageert of niet meer reageert. Zie voor stappen [Installatiegids > Onderhoudsmodus in- of uitschakelen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in onze ontwikkelaarsdocumentatie. Zorg ervoor om uw IP aan de Vrijgestelde IP adreslijst toe te voegen om ervoor te zorgen dat u nog tot uw plaats voor het oplossen van problemen kunt toegang hebben. Zie voor stappen [Handhaaf de lijst van vrijgestelde IP adressen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) in onze ontwikkelaarsdocumentatie.

<u>**Niet doen!**</u>

* Start aanvullende marketingcampagnes die extra pagina&#39;s naar uw site kunnen brengen.
* Voer indexen of extra kranen uit die extra belasting op de CPU of schijf kunnen veroorzaken.
* Voer belangrijke administratieve taken uit (bijvoorbeeld Commerce Admin, gegevensimport/export).
* Wis uw cache.

Uw site reageert mogelijk niet meer (als er nog geen site-uitval optreedt) als u een van de acties &quot;Niet uitvoeren&quot; uitvoert voordat u de oorzaak van de waarschuwing hebt onderzocht en opgelost.

## Oplossing

Volg deze stappen om de oorzaak te identificeren en problemen op te lossen.

>[!WARNING]
>
>Omdat dit een kritiek alarm is, adviseert het hoogst u voltooit **Stap 1** voordat u probeert het probleem op te lossen (stap 2 en volgende).

1. Controleer of er een Adobe Commerce-ondersteuningsticket bestaat. Zie voor stappen [Volg uw ondersteuningstickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in onze kennisbasis voor ondersteuning. De ondersteuning heeft mogelijk al een New Relic-drempelwaardewaarschuwing ontvangen, een ticket gemaakt en aan het probleem gewerkt. Als er geen ticket bestaat, maakt u er een. Het ticket moet de volgende informatie bevatten:
   * Reden van contactpersoon: selecteer &quot;KRITIEKE New Relic-waarschuwing ontvangen&quot;
   * Beschrijving van de signalering
   * [New Relic Incident Link](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dit is inbegrepen in uw [Beheerde waarschuwingen voor Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).

1. Gebruiken [New Relic APM&#39;s infrastructuurpagina](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) om de belangrijkste geheugenintensieve processen te identificeren. Raadpleeg New Relic voor meer informatie [Infrastructuurbewaking Hosts pagina > tabblad Processen](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes):
   * Als services zoals Redis, MySQL of PHP de belangrijkste bronnen van geheugenverbruik zijn, kunt u het volgende proberen:
1. Controleer of u de nieuwste versies hebt. In nieuwere versies kunnen soms geheugenlekken worden gecorrigeerd. Als u niet over de nieuwste versie beschikt, kunt u een upgrade uitvoeren. Raadpleeg voor stappen [Adobe Commerce on cloud Infrastructure > Services > Change Services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) in onze ontwikkelaarsdocumentatie.
1. Als het probleem met de service geen versiegerelateerd probleem is, probeert u het volgende:
1. **MySQL**: Controleren op problemen zoals langdurige query&#39;s, primaire sleutels niet gedefinieerd en dubbele indexen. Raadpleeg voor stappen [Meest voorkomende databaseproblemen in Adobe Commerce op cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) in onze kennisbasis voor ondersteuning.
1. **Redis**: Als Redis een van de belangrijkste bronnen van geheugenverbruik is, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
1. **PHP**: Als PHP een van de belangrijkste bronnen van geheugenverbruik is, kunt u lopende processen controleren door `ps aufx` in de CLI/terminal. In de eindoutput zult u cron banen en processen zien die momenteel worden uitgevoerd. Controleer de uitvoer op de uitvoeringstijd van het proces. Als er een kruin met een lange uitvoeringstijd is, kan de kruin hangen. Voor het oplossen van problemenstappen, zie [Trage prestaties, langzame en langlopende bekers](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) en [Cron job geplakt in status &quot;running&quot;](https://support.magento.com/hc/en-us/articles/360033099451) in onze kennisbasis voor ondersteuning.
1. Als u nog steeds moeite hebt om de bron van het probleem te identificeren, gebruikt u [Transactiepagina van New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) om transacties met prestatieproblemen te identificeren:
   * Transacties sorteren door oplopende Apdex-scores. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) verwijst naar tevredenheid van gebruikers over de responstijd van uw webtoepassingen en -services. A [lage Apdex-score](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) kan een knelpunt aangeven (een transactie met een hogere responstijd). Meestal is dit de database, Redis of PHP. Raadpleeg New Relic voor meer informatie [Transacties met de hoogste Apdex-ontevredenheid weergeven](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * De transacties van de soort door hoogste productie, de langzaamste gemiddelde reactietijd, het meest tijdrovend, en andere drempels. Raadpleeg New Relic voor meer informatie [Specifieke prestatieproblemen zoeken](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Als u het probleem nog steeds niet kunt identificeren, gebruikt u de pagina Infrastructuur van New Relic APM.
1. Als u niet de oorzaak van verhoogde geheugenconsumptie kunt identificeren, herzie recente tendensen om kwesties met recente codeplaatsingen of configuratieveranderingen (bijvoorbeeld, nieuwe klantengroepen en grote veranderingen in de catalogus) te identificeren. U wordt aangeraden de afgelopen 7 dagen van activiteit te controleren op correlaties in codeimplementaties of -wijzigingen.
1. Als de bovenstaande methoden u niet helpen de oorzaak en/of oplossing binnen een redelijke tijd te vinden, kunt u een upgrade aanvragen of de site in de onderhoudsmodus plaatsen als u dat nog niet hebt gedaan. Zie voor stappen [Tijdelijke wijziging aanvragen](/help/how-to/general/how-to-request-temporary-magento-upsize.md) in onze kennisbasis ter ondersteuning, en [Installatiegids > Onderhoudsmodus in- of uitschakelen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in onze ontwikkelaarsdocumentatie.
1. Als de upsize de plaats aan normale verrichtingen terugkeert, denk na om permanent te verzoeken (uw Team van de Rekening van de Adobe), of probeer om het probleem in uw Dedicated Staging te reproduceren door een ladingstest in werking te stellen en vragen te optimaliseren, of code die druk op de diensten vermindert. Zie [Adobe Commerce on cloud Infrastructure > Test Deployment > Load and stress testing](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) in onze ontwikkelaarsdocumentatie.
