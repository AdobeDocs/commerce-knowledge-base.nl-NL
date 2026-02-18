---
title: Algemene hulp bij het oplossen van problemen in de aangepaste module
description: In dit artikel wordt gesproken over algemene hulpmiddelen voor het oplossen van problemen met aangepaste modules in Adobe Commerce.
exl-id: c6603a2b-dc98-4022-ab29-c081c2b07415
feature: Extensions
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Algemene hulp bij het oplossen van problemen in de aangepaste module

In dit artikel wordt gesproken over algemene hulpmiddelen voor het oplossen van problemen met aangepaste modules in Adobe Commerce.

## Probleem

Als u zich realiseert is er een kwestie met de eigenschappen van uw douanemodule, en u krijgt geen duidelijke foutenmeldingen die de kwestie verklaren, dan zult u de logboeken van uw instantie willen raadplegen.

## Oplossing

Controleer de logboeken om te zien of zijn er ingangen met de naam van de douanemodule in de fout.  Afhankelijk van de betrokken fouten, kan de oplossing zich voorstellen, of u kunt uw nuttige het logboekinformatie van Adobe Commerce moeten omvatten als u a [&#x200B; Ticket van de Steun &#x200B;](https://experienceleague.adobe.com/nl/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) wilt openen. Zie de volgende alinea&#39;s voor informatie over de locatie van logbestanden en mogelijke oplossingen.

### Adobe Commerce (alle implementatiemethoden), Magento Open Source, alle 2.X-versies

1. De plaats van logboeken wordt geplaatst bij [&#x200B; Adobe Commerce op de logboeken van de het planarchitectuur van de wolkeninfrastructuur Pro &#x200B;](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) in onze steun kennisbasis.
1. Afhankelijk van de fouten die u vindt, als u een aangepaste module wilt in-, uitschakelen of verwijderen, bevatten deze artikelen details over deze handelingen:
   * [&#x200B; laat of maakt modules &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/tutorials/manage-modules) in onze ontwikkelaarsdocumentatie toe onbruikbaar.
   * [&#x200B; desinstalleert modules &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/tutorials/uninstall-modules) in onze ontwikkelaarsdocumentatie.

### Adobe Commerce op cloud-infrastructuur, alle versies

1. Logs plaatsen: [&#x200B; Adobe Commerce op de logboeken van de wolkeninfrastructuur &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/test/log-locations) in onze ontwikkelaarsdocumentatie.
1. Afhankelijk van de fouten die u vindt, als u een aangepaste module wilt in-, uitschakelen of verwijderen, bevatten deze artikelen in de ontwikkelaarsdocumentatie details over deze acties:
   * [&#x200B; installeer, beheer, en bevorder uitbreidingen &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure-store/extensions).
   * [&#x200B; de mislukte plaatsing van de Component &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/deploy/recover-failed-deployment).

## Gerelateerde lezing

In onze documentatie voor ontwikkelaars:

* [&#x200B; Overzicht van de Module &#x200B;](https://developer.adobe.com/commerce/php/architecture/modules/overview/)
* [&#x200B; Fouten die facultatieve steekproefgegevens installeren &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/errors-installing-optional-sample-data)
* [&#x200B; Uitzondering behandeling &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/develop/exceptions/)
* [&#x200B; Uitzonderingen tijdens installatie &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/exceptions-during-installation)
* [&#x200B; stel de Manager van de Module in werking &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/upgrade-guide/prepare/prerequisites)
* [&#x200B; de configuratiedossiers van de Module &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/files/module-files)
* [&#x200B; uit geheugenfouten &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade)
