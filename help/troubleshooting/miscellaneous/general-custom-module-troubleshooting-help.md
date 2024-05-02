---
title: Algemene hulp bij het oplossen van problemen in de aangepaste module
description: In dit artikel wordt gesproken over algemene hulpmiddelen voor het oplossen van problemen met aangepaste modules in Adobe Commerce.
exl-id: c6603a2b-dc98-4022-ab29-c081c2b07415
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Algemene hulp bij het oplossen van problemen in de aangepaste module

In dit artikel wordt gesproken over algemene hulpmiddelen voor het oplossen van problemen met aangepaste modules in Adobe Commerce.

## Probleem

Als u zich realiseert is er een kwestie met de eigenschappen van uw douanemodule, en u krijgt geen duidelijke foutenmeldingen die de kwestie verklaren, dan zult u de logboeken van uw instantie willen raadplegen.

## Oplossing

Controleer de logboeken om te zien of zijn er ingangen met de naam van de douanemodule in de fout.  Afhankelijk van de fouten kan de oplossing zichzelf voorstellen of moet u mogelijk uw nuttige Adobe Commerce-loggegevens opnemen als u een [Support-ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Zie de volgende alinea&#39;s voor informatie over de locatie van logbestanden en mogelijke oplossingen.

### Adobe Commerce (alle implementatiemethoden), Magento Open Source, alle 2.X-versies

1. Logboeklocaties:
   * [Adobe Commerce on cloud Infrastructure Starter-planningslogboeken](/help/how-to/general/log-locations-directories-for-starter-plan.md) in onze kennisbasis voor ondersteuning.
   * [Adobe Commerce on cloud Infrastructure Pro-planningslogbestanden](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) in onze kennisbasis voor ondersteuning.
1. Afhankelijk van de fouten die u vindt, als u een aangepaste module wilt in-, uitschakelen of verwijderen, bevatten deze artikelen details over deze handelingen:
   * [Modules in- of uitschakelen](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-enable.html) in onze ontwikkelaarsdocumentatie.
   * [Modules verwijderen](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-uninstall-mods.html) in onze ontwikkelaarsdocumentatie.

### Adobe Commerce op cloud-infrastructuur, alle versies

1. Logboeklocaties: [Adobe Commerce op cloud-infrastructuurlogs](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html) in onze ontwikkelaarsdocumentatie.
1. Afhankelijk van de fouten die u vindt, als u een aangepaste module wilt in-, uitschakelen of verwijderen, bevatten deze artikelen in de ontwikkelaarsdocumentatie details over deze acties:
   * [Extensies installeren, beheren en upgraden](https://devdocs.magento.com/guides/v2.3/cloud/howtos/install-components.html).
   * [Implementatiefout component](https://devdocs.magento.com/guides/v2.3/cloud/trouble/trouble_comp-deploy-fail.html).

## Gerelateerde lezing

In onze documentatie voor ontwikkelaars:

* [Overzicht van module](https://devdocs.magento.com/guides/v2.3/architecture/archi_perspectives/components/modules/mod_intro.html)
* [Fouten bij het installeren van optionele voorbeeldgegevens](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/tshoot_sample-data.html)
* [Uitzonderingsafhandeling](https://devdocs.magento.com/guides/v2.3/graphql/develop/exceptions.html)
* [Uitzonderingen tijdens installatie](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/tshoot_exceptions.html)
* [Module Manager uitvoeren](https://devdocs.magento.com/guides/v2.3/comp-mgr/module-man/compman-checklist.html)
* [Moduleconfiguratiebestanden](https://devdocs.magento.com/guides/v2.3/config-guide/config/config-files.html)
* [Onvoldoende geheugen](https://devdocs.magento.com/guides/v2.3/comp-mgr/trouble/cman/out-of-memory.html)
