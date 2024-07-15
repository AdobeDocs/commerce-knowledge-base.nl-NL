---
title: 'Beheerde waarschuwingen voor Adobe Commerce: waarschuwing voor een schijf'
description: Dit artikel bevat stappen voor het oplossen van problemen wanneer u een waarschuwing ontvangt voor Adobe Commerce in New Relic. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.
exl-id: 07b34db1-11ec-4cf2-ae47-cfc067f91383
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: d7dcb23eee8793b6b97717827feb88c09994bd8b
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# Beheerde waarschuwingen voor Adobe Commerce: waarschuwing voor een schijf

Dit artikel bevat stappen voor het oplossen van problemen wanneer u een waarschuwing ontvangt voor Adobe Commerce in New Relic. Er moet onmiddellijk actie worden ondernomen om dit probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.

![ waarschuwing van de schijfwaarschuwing ](assets/disk-warning-magento-managed.png){width="500"}

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, Pro-planarchitectuur.

## Probleem

U zult een alarm in New Relic ontvangen als u tot [ Beheerde alarm voor Adobe Commerce ](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) hebt ondertekend en één of meerdere waakzame drempels zijn overschreden. Deze waarschuwingen zijn door de Adobe ontwikkeld om klanten een standaardset te bieden met inzichten van support en engineering.

<u> **doe!** </u>

* Abort om het even welke plaatsing die tot dit alarm wordt gepland wordt ontruimd.
* Zet uw site onmiddellijk in de onderhoudsmodus als uw site helemaal niet reageert of niet meer reageert. Voor stappen verwijzen naar [ Gids van de Installatie > laat of maakt onderhoudswijze ](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) in onze ontwikkelaarsdocumentatie toe onbruikbaar. Zorg ervoor om uw IP aan de Vrijgestelde IP adreslijst toe te voegen om ervoor te zorgen dat u nog tot uw plaats voor het oplossen van problemen kunt toegang hebben. Voor stappen, verwijs naar [ handhaaf de lijst van vrijgestelde IP adressen ](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) in onze ontwikkelaarsdocumentatie.

<u> **niet!** </u>

* Start aanvullende marketingcampagnes die mogelijk extra paginaweergaven naar uw site brengen.
* Voer indexen of extra kranen uit die extra belasting op de CPU of schijf kunnen veroorzaken.
* Voer belangrijke administratieve taken uit (bijvoorbeeld Commerce Admin, gegevensimport/export).
* Wis uw cache. Uw site reageert mogelijk niet meer (als er nog geen site-uitval optreedt) als u een van de acties &quot;Niet uitvoeren&quot; uitvoert voordat u de oorzaak van de waarschuwing hebt onderzocht en opgelost.

## Oplossing

Volg deze stappen om de oorzaak te identificeren en problemen op te lossen:

1. Controleer in New Relic de schijven voor het beste gebruik. Voor stappen verwijzen naar het lusje van de Opslag op New Relic [ de pagina van de Gastheren van de Infrastructuur die ](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) controleert:
   * Als u in New Relic een trage toename van het schijfgebruik ziet, probeert u de volgende opties:
   * Schijfruimte optimaliseren door ruimtetoewijzing aan te passen. Voor stappen, verwijs naar [ beheer de ruimte van de Schijf ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) in onze ontwikkelaarsdocumentatie. Mogelijk moet u ook meer schijfruimte aanvragen (neem contact op met het accountteam van de Adobe).
   * Maak schijfruimte vrij voor MySQL. Verwijs naar [ MySQL schijfruimte is laag ](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) voor stappen.
   * Als New Relic een snel toenemend schijfgebruik laat zien, kan dit erop wijzen dat er een probleem is dat ertoe heeft geleid dat een bestand zeer snel is toegenomen in een map. Voer de volgende controles uit:
1. Controleer algemene schijfruimte om het probleem te identificeren door het volgende bevel in CLI/Terminal in werking te stellen: `df -h`
1. Nadat u een folder met onverwacht groot en toenemend schijfgebruik identificeert, moet u het beïnvloede dossiersysteem controleren. In het volgende voorbeeld wordt getoond hoe u de bestandsmap `pub/media/` kunt controleren. Dit is de map die Adobe Commerce gebruikt voor het opslaan van logbestanden en grote mediabestanden. U moet deze opdracht echter uitvoeren voor elke map waarin onverwacht schijfgebruik wordt getoond: `du -sch ~/pub/media/*` .

Als in de uitvoer van de terminal een bestand in een van deze mappen wordt weergegeven, neemt het schijfgebruik snel toe en weet u dat de inhoud van het bestand niet nodig is, kunt u het bestand verwijderen. Als u niet comfortabel het nemen van deze actie bent, [ voorleggen een de steunkaartje van Adobe Commerce ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
