---
title: 'Beheerde waarschuwingen voor Adobe Commerce: waarschuwing van de Apdex'
description: Dit artikel bevat stappen voor het oplossen van problemen wanneer u een waarschuwing van de Apdex voor Adobe Commerce in New Relic ontvangt. Met de Apdex-score wordt gemeten of gebruikers tevreden zijn met de responstijd van webtoepassingen en -services. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.
exl-id: 6e3f28ae-734b-468f-b6a5-c4f2edb1cb4b
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 3493214b468ac93dc938690495ea0a6bcf645a29
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 0%

---

# Beheerde waarschuwingen voor Adobe Commerce: waarschuwing van Apdex

Dit artikel bevat stappen voor het oplossen van problemen wanneer u een waarschuwing van de Apdex voor Adobe Commerce in New Relic ontvangt. Met de Apdex-score wordt gemeten of gebruikers tevreden zijn met de responstijd van webtoepassingen en -services. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.

![waarschuwing bij apdex](assets/apdex-warning-magento-managed.png){width="500"}

## Betrokken producten en versies

* Adobe Commerce on cloud Infrastructure Pro-planarchitectuur
* Adobe Commerce on cloud Infrastructure Starter-planarchitectuur

## Probleem

Je ontvangt een beheerde waarschuwing in New Relic als je je hebt aangemeld bij [Beheerde waarschuwingen voor Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) en een of meer alarmdrempels zijn overschreden. Deze waarschuwingen zijn door de Adobe ontwikkeld om handelaren een standaardset te bieden met inzichten van support en engineering.

<u> **Doe het!** </u>

* Abort om het even welke plaatsing die tot dit alarm wordt gepland wordt ontruimd.
* Zet uw site onmiddellijk in de onderhoudsmodus als uw site helemaal niet reageert of niet meer reageert. Raadpleeg voor stappen  [Installatiegids > Onderhoudsmodus in- of uitschakelen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in onze ontwikkelaarsdocumentatie. Zorg ervoor om uw IP aan de Vrijgestelde IP adreslijst toe te voegen om ervoor te zorgen dat u nog tot uw plaats voor het oplossen van problemen kunt toegang hebben. Raadpleeg voor stappen [Handhaaf de lijst van vrijgestelde IP adressen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) in onze ontwikkelaarsdocumentatie.

<u>**Niet doen!**</u>

* Start aanvullende marketingcampagnes die extra pagina&#39;s naar uw site kunnen brengen.
* Voer indexen of extra kranen uit die extra belasting op de CPU of schijf kunnen veroorzaken.
* Voer belangrijke administratieve taken uit (bijvoorbeeld Commerce Admin, gegevensimport/export).
* Wis uw cache.

## Oplossing

Volg deze stappen om de oorzaak te identificeren en problemen op te lossen.

1. Om de bron van het probleem te identificeren, gebruik [Transactiepagina van New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) om transacties met prestatieproblemen te identificeren:
   * Transacties sorteren door oplopende Apdex-scores. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) verwijst naar tevredenheid van gebruikers over de responstijd van uw webtoepassingen en -services. A [lage Apdex-score](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) kan een knelpunt aangeven (een transactie met een hogere responstijd). Meestal is dit de database, Redis of PHP. Raadpleeg New Relic voor meer informatie [Transacties met de hoogste Apdex-ontevredenheid weergeven](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * De transacties van de soort door hoogste productie, de langzaamste gemiddelde reactietijd, het meest tijdrovend, en andere drempels. Raadpleeg New Relic voor meer informatie [Specifieke prestatieproblemen zoeken](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Gebruiken [New Relic APM&#39;s infrastructuurpagina](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) identificeren van processen die veel bronnen vereisen. Raadpleeg New Relic voor meer informatie [Infrastructuurbewaking Hosts pagina > tabblad Processen](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Als de diensten zoals Redis of MySQL de hoogste bron van geheugenconsumptie zijn, probeer het volgende:
   * Controleer of u de meest recente versie hebt. In nieuwere versies kunnen soms geheugenlekken worden gecorrigeerd. Als u niet over de nieuwste versie beschikt, kunt u een upgrade uitvoeren. Raadpleeg voor stappen [Cloud voor Adobe Commerce > Services > Services wijzigen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) in onze ontwikkelaarsdocumentatie.
1. Als de kwestie niet door de dienstversies wordt veroorzaakt:
   * Controleren op andere MySQL-problemen, zoals langdurige query&#39;s, primaire sleutels niet gedefinieerd en dubbele indexen. Raadpleeg voor stappen [Meest voorkomende databaseproblemen in Adobe Commerce op cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) in onze kennisbasis voor ondersteuning.
   * Controleren op andere PHP problemen. Het runnen van processen van het overzicht door te lopen `ps aufx` in de CLI/terminal. In de eindoutput zult u cron banen en processen zien die momenteel worden uitgevoerd. Controleer de uitvoer op de uitvoeringstijd van het proces. Als er een kruin met een lange uitvoeringstijd is, kan de kruin hangen. Voor het oplossen van problemenstappen, verwijs naar [Trage prestaties, langzame en langlopende bekers](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) en [Cron job geplakt in status &quot;running&quot;](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) in onze kennisbasis voor ondersteuning.
1. Zodra een potentiële bron van de kwestie wordt geïdentificeerd, SSH in het milieu om verder te onderzoeken. Raadpleeg voor stappen [Cloud voor Adobe Commerce > Technologieën en vereisten > SSH in uw omgeving](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) in onze ontwikkelaarsdocumentatie.
1. Als u nog worstelt om de bron te identificeren, herzie recente tendensen om kwesties met recente codeplaatsingen of configuratieveranderingen (bijvoorbeeld, nieuwe klantengroepen en grote veranderingen in de catalogus) te identificeren. U wordt aangeraden de afgelopen zeven dagen van activiteit te controleren op correlaties in codeimplementaties of -wijzigingen.
1. Als u niet binnen een redelijke termijn een oplossing kunt vinden, verzoek om een vergrote of plaats in onderhoudswijze als u nog niet hebt gedaan. Raadpleeg voor stappen [Tijdelijke wijziging aanvragen](/help/how-to/general/how-to-request-temporary-magento-upsize.md) in onze kennisbasis ter ondersteuning, en [Installatiegids > Onderhoudsmodus in- of uitschakelen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in onze ontwikkelaarsdocumentatie.
1. Als de [vergroten](/help/how-to/general/how-to-request-temporary-magento-upsize.md) keert de plaats aan normale verrichtingen terug, denk na om permanent te verzoeken (uw Team van de Rekening van de Adobe contacteren), of probeer om het probleem in uw Dedicated Staging te reproduceren door een ladingstest in werking te stellen en vragen te optimaliseren, of code die druk op de diensten vermindert. Zie [Cloud voor Adobe Commerce > Testimplementatie > Laden en stresstesten](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) in onze ontwikkelaarsdocumentatie.
