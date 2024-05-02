---
title: 'Beheerde waarschuwingen voor Adobe Commerce: waarschuwing voor CPU'
description: Dit artikel bevat stappen voor het oplossen van problemen wanneer u een waarschuwing voor de processor ontvangt voor Adobe Commerce in New Relic. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.
exl-id: 03686684-3b7e-430a-a05a-a96f38345322
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# Beheerde waarschuwingen voor Adobe Commerce: waarschuwing voor CPU

Dit artikel bevat stappen voor het oplossen van problemen wanneer u een waarschuwing voor de processor ontvangt voor Adobe Commerce in New Relic. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.

![Waarschuwing CPU](assets/cpu-warning-magento-managed.png){width="500"}

## Betrokken producten en versies

Adobe Commerce on cloud Infrastructure Pro-planarchitectuur

## Probleem

Je ontvangt een bericht in New Relic als je je hebt aangemeld bij [Beheerde waarschuwingen voor Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) en een of meer alarmdrempels zijn overschreden. Deze waarschuwingen zijn door de Adobe ontwikkeld om klanten een standaardset te bieden met inzichten van support en engineering.

<u> **Doe het!** </u>

* Abort om het even welke plaatsing die tot dit alarm wordt gepland wordt ontruimd.
* Zet uw site onmiddellijk in de onderhoudsmodus als uw site helemaal niet reageert. Raadpleeg voor stappen [Installatiegids > Onderhoudsmodus in- of uitschakelen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in onze ontwikkelaarsdocumentatie. Zorg ervoor om uw IP aan de Vrijgestelde IP adreslijst toe te voegen om ervoor te zorgen dat u nog tot uw plaats voor het oplossen van problemen kunt toegang hebben. Raadpleeg voor stappen [Handhaaf de lijst van vrijgestelde IP adressen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) in onze ontwikkelaarsdocumentatie.

<u>**Niet doen!**</u>

* Start aanvullende marketingcampagnes die extra pagina&#39;s naar uw site kunnen brengen.
* Voer indexen of extra kranen uit die extra belasting op de CPU of schijf kunnen veroorzaken.
* Voer belangrijke administratieve taken uit (bijvoorbeeld Commerce Admin, gegevensimport/export).
* Wis uw cache.

## Oplossing

Volg deze stappen om de oorzaak te identificeren en problemen op te lossen.

1. Gebruiken [Transactiepagina van New Relic APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) om transacties met prestatieproblemen te identificeren:
   * Transacties sorteren door oplopende Apdex-scores. [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) verwijst naar tevredenheid van gebruikers over de responstijd van uw webtoepassingen en -services. [Een lage Apdex-score](/help/troubleshooting/miscellaneous/troubleshoot-performance-using-new-relic-on-magento-commerce.md#low_user_satisfaction) kan een knelpunt aangeven (een transactie met een hogere responstijd). Meestal is dit de database, Redis of PHP. Raadpleeg New Relic voor meer informatie [Transacties met de hoogste Apdex-ontevredenheid weergeven](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * De transacties van de soort door hoogste productie, langzaamste gemiddelde reactietijd, het meest tijdrovend, en andere drempels. Raadpleeg New Relic voor meer informatie [Specifieke prestatieproblemen zoeken](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Als u nog steeds moeite hebt om de bron te identificeren, gebruikt u [New Relic APM&#39;s infrastructuurpagina](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) het identificeren van hulpbron zware diensten. Raadpleeg New Relic voor meer informatie [Infrastructuurbewaking Hosts pagina > tabblad Processen](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Als u de bron identificeert, SSH in het milieu om verder te onderzoeken. Raadpleeg voor stappen [Cloud voor Adobe Commerce > SSH in uw omgeving](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) in onze ontwikkelaarsdocumentatie.
1. Als u nog steeds moeite hebt om de bron te identificeren:
   * Recente trends van het overzicht om kwesties met recente codeplaatsingen of configuratieveranderingen (bijvoorbeeld, nieuwe klantengroepen en grote veranderingen in de catalogus) te identificeren. U wordt aangeraden de afgelopen zeven dagen van activiteit te controleren op correlaties in codeimplementaties of -wijzigingen.
   * Overweeg om te controleren op en vlakke catalogi uit te schakelen. Raadpleeg voor stappen [Trage prestaties, langzame en langlopende bekers](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) in onze kennisbasis voor ondersteuning.
   * Als u vermoedt dat u een aanval van DDoS ervaart, probeer blokkerend beide verkeer. Raadpleeg voor stappen [Hoe te om kwaadwillig verkeer voor Adobe Commerce op Fastly te blokkeren](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) in onze kennisbasis voor ondersteuning.
1. Als het probleem tijdelijk lijkt, voert u reductiestappen uit zoals een upgrade of plaatst u de site in de onderhoudsmodus. Raadpleeg voor stappen [Tijdelijke wijziging aanvragen](/help/how-to/general/how-to-request-temporary-magento-upsize.md) in onze kennisbasis ter ondersteuning, en [Installatiegids > Onderhoudsmodus in- of uitschakelen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in onze ontwikkelaarsdocumentatie. Als de upsize de plaats aan normale verrichtingen terugkeert, overweeg om permanent te verzoeken (uw Team van de Rekening van de Adobe) of probeer om het probleem in uw Dedicated Staging te reproduceren door een ladingstest in werking te stellen en vragen te optimaliseren, of code die druk op de diensten vermindert. Raadpleeg voor stappen [Cloud voor Adobe Commerce > Testimplementatie > Laden en stresstesten](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) in onze ontwikkelaarsdocumentatie.
