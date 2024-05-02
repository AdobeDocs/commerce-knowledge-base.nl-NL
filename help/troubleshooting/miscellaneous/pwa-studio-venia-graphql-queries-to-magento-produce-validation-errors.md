---
title: "PWA Studio: vragen van Venia GraphQL aan Adobe Commerce leiden tot validatiefouten"
description: Dit artikel bevat aanbevelingen voor het oplossen van het probleem waarbij aanvragen van GraphQL naar Adobe Commerce-instanties in Venia storefront validatiefouten veroorzaken.
exl-id: ba268945-2a10-4af5-8089-cde21f0687bd
feature: GraphQL
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# PWA Studio: vragen van Venia GraphQL aan Adobe Commerce veroorzaken validatiefouten

Dit artikel bevat aanbevelingen voor het oplossen van het probleem waarbij aanvragen van GraphQL naar Adobe Commerce-instanties in Venia storefront validatiefouten veroorzaken.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.2.x, 2.3.x
* Adobe Commerce op cloud-infrastructuur 2.2.x, 2.3.x
* PWA Studio-project voor Adobe Commerce

## Probleem

Op vragen van Venia GraphQL aan Adobe Commerce op locatie of Adobe Commerce over cloudinfrastructuur worden validatiefouten gegenereerd.

## Oorzaak

Een van de oorzaken van het probleem kan zijn dat Venia en zijn GraphQL-query&#39;s niet meer overeenkomen met het schema van de aangesloten Adobe Commerce-instantie.

## Oplossing

Om te testen of uw vragen bijgewerkt zijn, stel het volgende bevel in de projectwortel in werking:

```bash
yarn run validate-queries
```

Dit zal een verenigbaarheidsrapport tonen. Als u incompatibiliteiten hebt, moet u uw PWA Studio of Adobe Commerce-exemplaar upgraden. Controleer de [Adobe Commerce-compatibiliteitsmatrix](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/version-compatibility/) om te zien welke versies u precies nodig hebt.

Verwijs naar de volgende documentatie voor instructies op hoe te om te bevorderen:

* Zoek voor upgrades van PWA Studio&#39;s naar de sectie &quot;Upgrade uitvoeren vanaf een vorige versie&quot; van het dialoogvenster [Opmerkingen bij de release PWA](https://github.com/magento/pwa-studio/releases/) voor de versie die u moet upgraden.
* [Adobe Commerce upgraden op versie van cloudinfrastructuur](https://devdocs.magento.com/cloud/project/project-upgrade.html) in onze documentatie voor ontwikkelaars
* [Upgrade uitvoeren van Adobe Commerce op locatie (geïnstalleerd met gebruik van &quot;composer create-project&quot; of archief)](https://devdocs.magento.com/guides/v2.3/comp-mgr/cli/cli-upgrade.html) in onze documentatie voor ontwikkelaars
* [Upgrade uitvoeren van Adobe Commerce op locatie (geïnstalleerd door Adobe Commerce repo te klonen)](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/dev_update-magento.html) in onze documentatie voor ontwikkelaars

## Gerelateerde lezing

* [PWA Studio: Webpack loopt vast voordat de compilatie wordt gestart](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md) in onze kennisbasis voor ondersteuning
* [PWA Studio: validatiefouten bij het uitvoeren van de ontwikkelaarsmodus](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md) in onze kennisbasis voor ondersteuning
* [PWA Studio: browser geeft &quot;Cannot proxy to&quot;error weer](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md) in onze kennisbasis voor ondersteuning
* [Vorm NPM om PWA Studio te kunnen gebruiken](/help/how-to/general/configure-npm-to-be-able-to-use-pwa-studio.md) in onze kennisbasis voor ondersteuning
* [PWA voor Adobe Commerce-documentatie](https://magento.github.io/pwa-studio/)
