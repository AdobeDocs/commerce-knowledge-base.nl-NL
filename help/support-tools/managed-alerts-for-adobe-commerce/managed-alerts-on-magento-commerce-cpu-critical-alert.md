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

![ schijf kritiek alarm ](assets/cpu-critical-magento-managed.png){width="500"}

## Betrokken producten en versies

Adobe Commerce on cloud Infrastructure Pro-planarchitectuur

## Probleem

U zult een beheerd alarm in New Relic ontvangen als u tot [ Beheerde alarm voor Adobe Commerce ](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) hebt ondertekend en één of meerdere waakzame drempels zijn overschreden. Deze waarschuwingen zijn door Adobe Commerce ontwikkeld om klanten een standaardset te bieden met inzichten van support en engineering.

<u>**doe!**</u>:

* Abort om het even welke plaatsing die tot dit alarm wordt gepland wordt ontruimd.
* Zet uw site onmiddellijk in de onderhoudsmodus als uw site helemaal niet reageert of niet meer reageert. Voor stappen, verwijs naar [ Gids van de Installatie > laat of maakt onderhoudswijze ](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in onze ontwikkelingsdocumentatie toe onbruikbaar. Zorg ervoor om uw IP aan de Vrijgestelde IP adreslijst toe te voegen om ervoor te zorgen dat u nog tot uw plaats voor het oplossen van problemen kunt toegang hebben. Voor stappen, verwijs naar [ handhaaf de lijst van vrijgestelde IP adressen ](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) in onze ontwikkelaarsdocumentatie.

<u>**niet!**</u>:

* Start aanvullende marketingcampagnes die extra pagina&#39;s naar uw site kunnen brengen.
* Voer indexen of extra kranen uit, wat extra belasting op de CPU of schijf kan veroorzaken.
* Voer belangrijke administratieve taken uit (zoals de Commerce Admin, gegevensimport/export).
* Wis uw cache.

Uw site reageert mogelijk niet meer (als u nog geen site-uitval hebt) als u een van de acties &quot;Niet uitvoeren&quot; uitvoert voordat u de oorzaak van de waarschuwing hebt onderzocht en opgelost.

## Oplossing

Volg deze stappen om de oorzaak te identificeren en problemen op te lossen.

>[!WARNING]
>
>Omdat dit een kritiek alarm is, wordt het hoogst geadviseerd u **Stap 1** voltooit alvorens u probeert om de kwestie (Stap 2 vanaf) problemen op te lossen.

Controleer of het Adobe Commerce-ondersteuningsticket bestaat. Voor stappen, verwijs naar [ Spoor uw steunkaartjes ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in onze basis van de steunkennis. De ondersteuning heeft mogelijk een New Relic-drempelwaardewaarschuwing ontvangen, een ticket gemaakt en aan het probleem gewerkt. Als er geen ticket bestaat, maakt u er een. Het ticket moet de volgende informatie bevatten:

1. Reden van contactpersoon: selecteer &quot;KRITIEK New Relic-bericht ontvangen&quot;.
1. Beschrijving van de signalering.
1. [ verbinding van het Ongeval van New Relic ](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dit is inbegrepen in uw [ Beheerde alarm voor Adobe Commerce ](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. De pagina van de Transactie van New Relic APM van het gebruik ](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) om transacties met prestatieskwesties te identificeren:[
   * Transacties sorteren door oplopende Apdex-scores. [ Apdex ](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) verwijst naar gebruikerstevredenheid aan de reactietijd van uw Webtoepassingen en de diensten. A [ lage score van de Index ](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) kan op een knelpunt (een transactie met een hogere reactietijd) wijzen. Gewoonlijk is dit gerelateerd aan de database, Redis of PHP. Voor stappen, verwijs naar de transacties van de Mening van New Relic [ met de hoogste ontevredenheid van de Index ](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * De transacties van de soort door hoogste productie, langzaamste gemiddelde reactietijd, het meest tijdrovend, en andere drempels. Voor stappen, verwijs naar New Relic [ vind specifieke prestatiesproblemen ](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Als u nog worstelt om de bron te identificeren, gebruik [ de pagina van de Infrastructuur van New Relic APM ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page) om middel-zware diensten te identificeren. Voor stappen, verwijs naar de pagina van de Gastheren van de Infrastructuur van New Relic [ controle > het lusje van Processen ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Als u de bron identificeert, SSH in het milieu om verder te onderzoeken. Voor stappen, verwijs naar [ SSH in uw milieu voor Adobe Commerce op wolkeninfrastructuur ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) in onze ontwikkelaarsdocumentatie.
1. Als u nog steeds moeite hebt om de bron te identificeren:
   * Recente trends van het overzicht om kwesties met recente codeplaatsingen of configuratieveranderingen (bijvoorbeeld, nieuwe klantengroepen en grote veranderingen in de catalogus) te identificeren. U wordt aangeraden de afgelopen zeven dagen van activiteit te controleren op correlaties in codeimplementaties of -wijzigingen.
   * Overweeg om te controleren op en vlakke catalogi uit te schakelen. Voor stappen, verwijs naar [ Trage prestaties, langzame en lange lopende kronen ](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) in onze basis van de steunkennis.
   * Als u vermoedt dat u een aanval van DDoS ervaart, probeer blokkerend beide verkeer. Voor stappen, verwijs naar [ hoe te om kwaadwillig verkeer voor Adobe Commerce op wolkeninfrastructuur op Fastly niveau ](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) in onze steunkennisbasis te blokkeren.
1. Als het probleem tijdelijk lijkt, voert u reductiestappen uit zoals een upgrade of plaatst u de site in de onderhoudsmodus. Voor stappen, verwijs naar [ hoe te om tijdelijk te verzoeken resize ](/help/how-to/general/how-to-request-temporary-magento-upsize.md) in onze steunkennisbasis en [ Gids van de Installatie > laat of maakt onderhoudswijze ](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in onze ontwikkelaarsdocumentatie toe onbruikbaar. Als de upsize de plaats aan normale verrichtingen terugkeert, overweeg om permanent te verzoeken (uw Team van de Rekening van de Adobe) of probeer om het probleem in uw Dedicated Staging te reproduceren door een ladingstest in werking te stellen en vragen of code te optimaliseren die druk op de diensten vermindert. Voor stappen, verwijs naar [ Plaatsing van de Test > het Testen van de Lading en van de stress ](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) in onze ontwikkelaarsdocumentatie voor Adobe Commerce op wolkeninfrastructuur.
