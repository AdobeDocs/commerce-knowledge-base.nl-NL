---
title: 'Beheerde waarschuwingen over Adobe Commerce: CPU-kritieke waarschuwing'
description: Dit artikel bevat stappen voor het oplossen van problemen wanneer u een kritieke waarschuwing voor Adobe Commerce in New Relic ontvangt. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.
exl-id: 45b8ced0-b12f-428b-9838-2a9c26b9874b
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 5be8f2969426078bfcc0e4ffb4895dcf0327165f
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 0%

---

# Beheerde waarschuwingen over Adobe Commerce: kritieke CPU-waarschuwing

Dit artikel bevat stappen voor het oplossen van problemen wanneer u een kritieke waarschuwing voor Adobe Commerce in New Relic ontvangt. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.

![kritieke schijf-waarschuwing](assets/cpu-critical-magento-managed.png){width="500"}

## Betrokken producten en versies

Adobe Commerce on cloud Infrastructure Pro-planarchitectuur

## Probleem

Je ontvangt een beheerde waarschuwing in New Relic als je je hebt aangemeld bij [Beheerde waarschuwingen voor Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) en een of meer alarmdrempels zijn overschreden. Deze waarschuwingen zijn door Adobe Commerce ontwikkeld om klanten een standaardset te bieden met inzichten van support en engineering.

<u>**Doe het!**</u>:

* Abort om het even welke plaatsing die tot dit alarm wordt gepland wordt ontruimd.
* Zet uw site onmiddellijk in de onderhoudsmodus als uw site helemaal niet reageert of niet meer reageert. Raadpleeg voor stappen [Installatiegids > Onderhoudsmodus in- of uitschakelen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in onze ontwikkelaarsdocumentatie. Zorg ervoor om uw IP aan de Vrijgestelde IP adreslijst toe te voegen om ervoor te zorgen dat u nog tot uw plaats voor het oplossen van problemen kunt toegang hebben. Raadpleeg voor stappen [Handhaaf de lijst van vrijgestelde IP adressen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) in onze ontwikkelaarsdocumentatie.

<u>**Niet doen!**</u>:

* Start aanvullende marketingcampagnes die extra pagina&#39;s naar uw site kunnen brengen.
* Voer indexen of extra kranen uit, wat extra belasting op de CPU of schijf kan veroorzaken.
* Voer belangrijke administratieve taken uit (zoals de Commerce Admin, gegevensimport/export).
* Wis uw cache.

Uw site reageert mogelijk niet meer (als u nog geen site-uitval hebt) als u een van de acties &quot;Niet uitvoeren&quot; uitvoert voordat u de oorzaak van de waarschuwing hebt onderzocht en opgelost.

## Oplossing

Volg deze stappen om de oorzaak te identificeren en problemen op te lossen.

>[!WARNING]
>
>Omdat dit een kritiek alarm is, adviseert het hoogst u voltooit **Stap 1** voordat u probeert het probleem op te lossen (stap 2 en volgende).

Controleer of het Adobe Commerce-ondersteuningsticket bestaat. Raadpleeg voor stappen [Volg uw ondersteuningstickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in onze kennisbasis voor ondersteuning. De ondersteuning heeft mogelijk een New Relic-drempelwaardewaarschuwing ontvangen, een ticket gemaakt en aan het probleem gewerkt. Als er geen ticket bestaat, maakt u er een. Het ticket moet de volgende informatie bevatten:

1. Reden van contactpersoon: selecteer &quot;KRITIEK New Relic-bericht ontvangen&quot;.
1. Beschrijving van de signalering.
1. [New Relic Incident Link](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dit is inbegrepen in uw [Beheerde waarschuwingen voor Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Gebruiken [Transactiepagina van New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) om transacties met prestatieproblemen te identificeren:
   * Transacties sorteren door oplopende Apdex-scores. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) verwijst naar tevredenheid van gebruikers over de responstijd van uw webtoepassingen en -services. A [lage Apdex-score](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) kan een knelpunt aangeven (een transactie met een hogere responstijd). Gewoonlijk is dit gerelateerd aan de database, Redis of PHP. Raadpleeg New Relic voor meer informatie [Transacties met de hoogste Apdex-ontevredenheid weergeven](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * De transacties van de soort door hoogste productie, langzaamste gemiddelde reactietijd, het meest tijdrovend, en andere drempels. Raadpleeg New Relic voor meer informatie [Specifieke prestatieproblemen zoeken](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Als u nog steeds moeite hebt om de bron te identificeren, gebruikt u [New Relic APM&#39;s infrastructuurpagina](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page) het identificeren van hulpbronnenintensieve diensten. Raadpleeg New Relic voor meer informatie [Infrastructuurbewaking Hosts pagina > tabblad Processen](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Als u de bron identificeert, SSH in het milieu om verder te onderzoeken. Raadpleeg voor stappen [SSH in uw omgeving voor Adobe Commerce op cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) in onze ontwikkelaarsdocumentatie.
1. Als u nog steeds moeite hebt om de bron te identificeren:
   * Recente trends van het overzicht om kwesties met recente codeplaatsingen of configuratieveranderingen (bijvoorbeeld, nieuwe klantengroepen en grote veranderingen in de catalogus) te identificeren. U wordt aangeraden de afgelopen zeven dagen van activiteit te controleren op correlaties in codeimplementaties of -wijzigingen.
   * Overweeg om te controleren op en vlakke catalogi uit te schakelen. Raadpleeg voor stappen [Trage prestaties, langzame en langlopende bekers](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) in onze kennisbasis voor ondersteuning.
   * Als u vermoedt dat u een aanval van DDoS ervaart, probeer blokkerend beide verkeer. Raadpleeg voor stappen [Hoe kan ik kwaadwillig verkeer voor Adobe Commerce op cloudinfrastructuur op snelniveau blokkeren](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) in onze kennisbasis voor ondersteuning.
1. Als het probleem tijdelijk lijkt, voert u reductiestappen uit zoals een upgrade of plaatst u de site in de onderhoudsmodus. Raadpleeg voor stappen [Tijdelijke wijziging aanvragen](/help/how-to/general/how-to-request-temporary-magento-upsize.md) in onze ondersteunende kennisbasis en [Installatiegids > Onderhoudsmodus in- of uitschakelen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in onze ontwikkelaarsdocumentatie. Als de upsize de plaats aan normale verrichtingen terugkeert, overweeg om permanent te verzoeken (uw Team van de Rekening van de Adobe) of probeer om het probleem in uw Dedicated Staging te reproduceren door een ladingstest in werking te stellen en vragen of code te optimaliseren die druk op de diensten vermindert. Raadpleeg voor stappen [Implementatie testen > Laden en stresstests](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) in onze ontwikkelaarsdocumentatie voor Adobe Commerce over cloudinfrastructuur.
