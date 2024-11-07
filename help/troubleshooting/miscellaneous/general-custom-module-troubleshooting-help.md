---
title: Algemene hulp bij het oplossen van problemen in de aangepaste module
description: In dit artikel wordt gesproken over algemene hulpmiddelen voor het oplossen van problemen met aangepaste modules in Adobe Commerce.
exl-id: c6603a2b-dc98-4022-ab29-c081c2b07415
feature: Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Algemene hulp bij het oplossen van problemen in de aangepaste module

In dit artikel wordt gesproken over algemene hulpmiddelen voor het oplossen van problemen met aangepaste modules in Adobe Commerce.

## Probleem

Als u zich realiseert is er een kwestie met de eigenschappen van uw douanemodule, en u krijgt geen duidelijke foutenmeldingen die de kwestie verklaren, dan zult u de logboeken van uw instantie willen raadplegen.

## Oplossing

Controleer de logboeken om te zien of zijn er ingangen met de naam van de douanemodule in de fout.  Afhankelijk van de betrokken fouten, kan de oplossing zich voorstellen, of u kunt uw nuttige het logboekinformatie van Adobe Commerce moeten omvatten als u a [ Ticket van de Steun ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) wilt openen. Zie de volgende alinea&#39;s voor informatie over de locatie van logbestanden en mogelijke oplossingen.

### Adobe Commerce (alle implementatiemethoden), Magento Open Source, alle 2.X-versies

1. Logboeklocaties:
   * [ Adobe Commerce op de logboeken van de het planarchitectuur van de Aanzet van de wolkeninfrastructuur ](/help/how-to/general/log-locations-directories-for-starter-plan.md) in onze basis van steunkennis.
   * [ Adobe Commerce op de logboeken van de de planarchitectuur van de wolkeninfrastructuur Pro ](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) in onze basis van de steunkennis.
1. Afhankelijk van de fouten die u vindt, als u een aangepaste module wilt in-, uitschakelen of verwijderen, bevatten deze artikelen details over deze handelingen:
   * [ laat of maakt modules ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/manage-modules) in onze ontwikkelaarsdocumentatie toe onbruikbaar.
   * [ desinstalleert modules ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules) in onze ontwikkelaarsdocumentatie.

### Adobe Commerce op cloud-infrastructuur, alle versies

1. Logs plaatsen: [ Adobe Commerce op de logboeken van de wolkeninfrastructuur ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) in onze ontwikkelaarsdocumentatie.
1. Afhankelijk van de fouten die u vindt, als u een aangepaste module wilt in-, uitschakelen of verwijderen, bevatten deze artikelen in de ontwikkelaarsdocumentatie details over deze acties:
   * [ installeer, beheer, en bevorder uitbreidingen ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions).
   * [ de mislukte plaatsing van de Component ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/recover-failed-deployment).

## Gerelateerde lezing

In onze documentatie voor ontwikkelaars:

* [ Overzicht van de Module ](https://developer.adobe.com/commerce/php/architecture/modules/overview/)
* [ Fouten die facultatieve steekproefgegevens installeren ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/errors-installing-optional-sample-data)
* [ Uitzondering behandeling ](https://developer.adobe.com/commerce/webapi/graphql/develop/exceptions/)
* [ Uitzonderingen tijdens installatie ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/exceptions-during-installation)
* [ stel de Manager van de Module in werking ](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/prerequisites)
* [ de configuratiedossiers van de Module ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/module-files)
* [ uit geheugenfouten ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade)
