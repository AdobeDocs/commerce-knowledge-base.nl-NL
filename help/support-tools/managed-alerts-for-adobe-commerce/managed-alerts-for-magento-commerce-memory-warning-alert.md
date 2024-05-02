---
title: 'Beheerde waarschuwingen voor Adobe Commerce: waarschuwing voor het geheugengebruik'
description: In dit artikel worden stappen beschreven voor het oplossen van problemen wanneer u een waarschuwing ontvangt voor Adobe Commerce in New Relic. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.
exl-id: bb5eb3f4-b162-4737-93d5-4037f2844bb1
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 8ef51d4e6d6efa51ad4b328a48b84e10c73f3ac6
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 0%

---

# Beheerde waarschuwingen voor Adobe Commerce: waarschuwing voor geheugenmeldingen

In dit artikel worden stappen beschreven voor het oplossen van problemen wanneer u een waarschuwing ontvangt voor Adobe Commerce in New Relic. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.

![geheugenwaarschuwing](assets/memory-warning-magento-managed.png){width="500"}

## Betrokken producten en versies

Adobe Commerce on cloud Infrastructure Pro-planarchitectuur

## Probleem

Je ontvangt een bericht in New Relic als je je hebt aangemeld bij [Beheerde waarschuwingen voor Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) en een of meer alarmdrempels zijn overschreden. Deze waarschuwingen zijn door Adobe Commerce ontwikkeld om klanten een standaardset te bieden met inzichten van support en engineering.

<u>**Doe het!**</u>:

* Het wordt aanbevolen om elke geplande implementatie af te breken totdat deze waarschuwing wordt gewist.
* Zet uw site onmiddellijk in de onderhoudsmodus als uw site helemaal niet reageert of niet meer reageert. Raadpleeg voor stappen [Installatiegids > Onderhoudsmodus in- of uitschakelen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in onze ontwikkelaarsdocumentatie. Zorg ervoor om uw IP aan de Vrijgestelde IP adreslijst toe te voegen om ervoor te zorgen dat u nog tot uw plaats voor het oplossen van problemen kunt toegang hebben. Raadpleeg voor stappen [Handhaaf de lijst van vrijgestelde IP adressen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) in onze ontwikkelaarsdocumentatie.

<u>**Niet doen!**</u>:

* Start aanvullende marketingcampagnes die extra pagina&#39;s naar uw site kunnen brengen.
* Voer indexen of extra kranen uit, wat extra belasting op de CPU of schijf kan veroorzaken.
* Voer belangrijke administratieve taken uit (bijv. de beheerder, gegevensimport/export).
* Wis uw cache.

## Oplossing

Volg deze stappen om de oorzaak te identificeren en problemen op te lossen.

1. Gebruiken [New Relic APM&#39;s infrastructuurpagina](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) om de belangrijkste geheugenintensieve processen te identificeren. Raadpleeg New Relic voor meer informatie [Infrastructuurbewaking Hosts pagina > tabblad Processen](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes). Als de diensten zoals Redis of MySQL de hoogste bron van geheugenconsumptie zijn, probeer het volgende:

   * Controleer of u de meest recente versie hebt. In nieuwere versies kunnen soms geheugenlekken worden gecorrigeerd. Als u niet over de nieuwste versie beschikt, kunt u een upgrade uitvoeren. Raadpleeg voor stappen [Adobe Commerce on cloud Infrastructure > Services > Change Services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) in onze ontwikkelaarsdocumentatie.
   * Als u nog steeds de bron van verhoogd geheugenverbruik niet kunt identificeren, controleert u op MySQL-problemen zoals langdurige query&#39;s, primaire sleutels niet gedefinieerd en dubbele indexen. Raadpleeg voor stappen [Meest voorkomende databaseproblemen in Adobe Commerce op cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) in onze kennisbasis voor ondersteuning.
   * Als er geen MySQL problemen zijn, controleer dan op PHP problemen. Het runnen van processen van het overzicht door te lopen `ps aufx` in de CLI/terminal. In de eindoutput, zult u cron banen en processen zien die momenteel worden uitgevoerd. Controleer de uitvoer op de uitvoeringstijd van het proces. Als er een kruin met een lange uitvoeringstijd is, kan de kruin hangen. Zie [Trage prestaties, langzame en langlopende bekers](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) en [Cron job geplakt in status &quot;running&quot;](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) in onze steun kennisbasis voor het oplossen van problemenstappen.

1. Als u nog steeds moeite hebt om de bron van het probleem te identificeren, gebruikt u [Transactiepagina van New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) om transacties met prestatieproblemen te identificeren:

   * Transacties sorteren door oplopende Apdex-scores. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) verwijst naar tevredenheid van gebruikers over de responstijd van uw webtoepassingen en -services. A [lage Apdex-score](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) kan een knelpunt aangeven (een transactie met een hogere responstijd). Meestal is dit de database, Redis of PHP. Raadpleeg New Relic voor meer informatie [Transacties met de hoogste Apdex-ontevredenheid weergeven](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * De transacties van de soort door hoogste productie, de langzaamste gemiddelde reactietijd, het meest tijdrovend, en andere drempels. Raadpleeg New Relic voor meer informatie [Specifieke prestatieproblemen zoeken](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Als u het probleem nog steeds niet kunt identificeren, gebruikt u de pagina Infrastructuur van New Relic APM.

1. Als u niet de oorzaak van verhoogde geheugenconsumptie kunt identificeren, herzie recente tendensen om kwesties met recente codeplaatsingen of configuratieveranderingen (bijvoorbeeld, nieuwe klantengroepen en grote veranderingen in de catalogus) te identificeren. U wordt aangeraden de afgelopen zeven dagen van activiteit te controleren op correlaties in codeimplementaties of -wijzigingen.

1. Als de bovenstaande methoden u niet helpen de oorzaak en/of oplossing binnen een redelijke tijd te vinden, vraagt u om een upgrade of zet u de site in de onderhoudsmodus als u dat nog niet hebt gedaan. Raadpleeg voor stappen [Tijdelijke wijziging aanvragen](/help/how-to/general/how-to-request-temporary-magento-upsize.md) in onze ondersteunende kennisbasis en [Installatiegids > Onderhoudsmodus in- of uitschakelen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in onze ontwikkelaarsdocumentatie.

1. Als de upsize de plaats aan normale verrichtingen terugkeert, denk na om permanent te verzoeken (uw Team van de Rekening van de Adobe), of probeer om het probleem in uw Dedicated Staging te reproduceren door een ladingstest in werking te stellen en vragen te optimaliseren, of code die druk op de diensten vermindert. Zie [Adobe Commerce on cloud Infrastructure > Test Deployment > Load and stress testing](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) in onze ontwikkelaarsdocumentatie.
