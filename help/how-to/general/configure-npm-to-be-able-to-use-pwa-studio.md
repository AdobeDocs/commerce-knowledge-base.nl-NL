---
title: Vorm NPM om PWA Studio te kunnen gebruiken
description: '[Progressieve Web Apps (PWA) Studio](https://magento.github.io/pwa-studio/) is een nieuw project beschikbaar voor Adobe Commerce op wolkeninfrastructuur 2.3.x of later. Om PWA Studio te kunnen gebruiken en installeren, moet u de versie van het NPM pakketbeheer aan 5.x of recenter plaatsen om steun voor Node.js 8.x te krijgen. Dit wordt gedaan in de sectie &grave; haks:build'' van het &grave;.magento.app.yaml &grave;- configuratiedossier.'
exl-id: 3854fc94-e8ad-45d8-bf3e-73462364220d
source-git-commit: 37ac9cca1f876a48092467aa38f2f2f013c83dd9
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Vorm NPM om PWA Studio te kunnen gebruiken

[ de Progressieve Studio van het Web Apps (PWA) ](https://magento.github.io/pwa-studio/) is een nieuw project beschikbaar voor Adobe Commerce op wolkeninfrastructuur 2.3.x of later. Om PWA Studio te kunnen gebruiken en installeren, moet u de versie van het NPM pakketbeheer aan 5.x of recenter plaatsen om steun voor Node.js 8.x te krijgen. Dit wordt gedaan in de `hooks:build` sectie van het `.magento.app.yaml` configuratiedossier.

## Milieu en technologieën

* Adobe Commerce op cloudinfrastructuur 2.3.X
* PWA voor Adobe Commerce

## NPM-versie instellen: stappen

Als u de benodigde NPM-versie wilt instellen, geeft u deze op in het configuratiebestand van `.magento.app.yaml` . Voer de volgende stappen uit:

1. Zoek in uw lokale ontwikkelomgeving het configuratiebestand van `.magento.app.yaml` .
1. Open het bestand voor bewerking met de teksteditor zonder opmaak of IDE.
1. Stel de vereiste versie in de sectie `hooks:build` in. In het volgende voorbeeld wordt de configuratie ingesteld op de installatie van NPM v9.5.0, de hoogste configuratie die momenteel beschikbaar is (4 februari 2019):

   ```yaml
   hooks:
       build: |
           unset NPM_CONFIG_PREFIX
           curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
           export NVM_DIR="$HOME/.nvm"
           [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
           nvm install 9.5.0
   ```

   >[!NOTE]
   >
   >Als u Node.JS in uw toepassing en niet alleen in uw bouwstijl wilt in werking stellen, te voegen gelieve de volgende bevelen toe om uw bouwstijlhaak te veranderen:
   > 
   > ```
   > echo 'unset NPM_CONFIG_PREFIX' >> .environment
   > echo 'export NO_UPDATE_NOTIFIER=1' >> .environment
   > echo 'export NVM_DIR="$MAGENTO_CLOUD_DIR/.nvm"' >> .environment
   > echo '[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"' >> .environment
   > ```

1. Sla de wijzigingen op in het bestand.
1. Git duw het uitgegeven dossier aan uw [ integratiemilieu ](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md).

De wijzigingen worden van kracht nadat u het bijgewerkte YAML-bestand in de omgeving hebt geplaatst.

## Gerelateerde documentatie

* [ configuratie van de Toepassing: haken ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/hooks-property.html?lang=nl-NL) in onze Adobe Commerce op de Gids van de Infrastructuur van de Wolk.
