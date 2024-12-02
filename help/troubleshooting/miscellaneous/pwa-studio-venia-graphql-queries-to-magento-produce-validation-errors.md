---
title: 'PWA Studio: vragen van Venia GraphQL aan Adobe Commerce veroorzaken validatiefouten'
description: Dit artikel bevat aanbevelingen voor het oplossen van het probleem waarbij aanvragen van GraphQL naar Adobe Commerce-instanties in Venia storefront validatiefouten veroorzaken.
exl-id: ba268945-2a10-4af5-8089-cde21f0687bd
feature: GraphQL
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Dit zal een verenigbaarheidsrapport tonen. Als u incompatibiliteiten hebt, moet u uw PWA Studio of Adobe Commerce-exemplaar upgraden. Controleer de [ de verenigbaarheidsmatrijs van Adobe Commerce ](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/version-compatibility/) om te zien welke precies versies u nodig hebt.

Verwijs naar de volgende documentatie voor instructies op hoe te om te bevorderen:

* Voor de verbeteringen van de PWA Studio, onderzoek naar &quot;Bevorderend van een vorige versie&quot;sectie van de [ versienota&#39;s van de PWA ](https://github.com/magento/pwa-studio/releases/) voor de versie die u moet bevorderen aan.
* [ Verbetering Adobe Commerce op versie van de wolkeninfrastructuur ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) in onze ontwikkelaarsdocumentatie
* [ Verbetering Adobe Commerce op-gebouw (geïnstalleerd gebruikend &quot;composer creeer-project&quot;of archief) ](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) in onze ontwikkelaarsdocumentatie
* [ Verbetering Adobe Commerce op-gebouw (die door het klonen van Adobe Commerce repo wordt geïnstalleerd) ](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/developer/git-installs) in onze ontwikkelaarsdocumentatie

## Gerelateerde lezing

* [ PWA Studio: Webpack hangt alvorens compilatie ](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md) in onze basis van de steunkennis te beginnen
* [ PWA Studio: De fouten van de Bevestiging wanneer het runnen van ontwikkelaarwijze ](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md) in onze basis van de steunkennis
* [ PWA Studio: Browser toont &quot;niet volmacht aan&quot;fout ](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md) in onze basis van de steunkennis
* [ vorm NPM om PWA Studio ](/help/how-to/general/configure-npm-to-be-able-to-use-pwa-studio.md) in onze basis van de steunkennis te kunnen gebruiken
* [ PWA voor de Documentatie van Adobe Commerce ](https://magento.github.io/pwa-studio/)
