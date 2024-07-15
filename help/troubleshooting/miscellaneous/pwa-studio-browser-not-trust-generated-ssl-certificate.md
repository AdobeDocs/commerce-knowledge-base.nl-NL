---
title: 'PWA Studio: browser vertrouwt gegenereerd SSL-certificaat niet'
description: Dit artikel biedt een oplossing voor een niet-vertrouwde, gegenereerde SSL-certificaatwaarschuwing in uw browser wanneer u tijdens de ontwikkeling naar een lokale instantie van uw PWA Studio-winkel navigeert.
exl-id: b7bfe1e6-5832-4472-9e51-f04b8583428a
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# PWA Studio: browser vertrouwt gegenereerd SSL-certificaat niet

Dit artikel biedt een oplossing voor een niet-vertrouwde, gegenereerde SSL-certificaatwaarschuwing in uw browser wanneer u tijdens de ontwikkeling naar een lokale instantie van uw PWA Studio-winkel navigeert.

## Betrokken producten en versies

PWA Studio voor Adobe Commerce

## Probleem

De browser vertrouwt het gegenereerde SSL-certificaat van uw lokale PWA Studio-winkel niet.

## Oorzaak

Naar de site voor ontwikkelen/opvoeren bladeren.

## Oplossing

Voer in uw storefront-project de opdracht uit voor het toevoegen van een aangepaste hostnaam en een SSL-certificaat aan uw lokale ontwikkelingsinstantie:

```sh
yarn buildpack create-custom-origin ./
```

Het produceren van certificaten wordt behandeld door [ devcert ](https://github.com/davewasmer/devcert). Het hangt van OpenSSL af, dus zorg ervoor u een huidige versie van open op uw systeem gebruikend het volgende bevel hebt:

`openssl version`

De versie moet 1.0 of hoger zijn (of LibreSSL 2 in het geval van OSX High Sierra).

U kunt hogere versies van OpenSSL met [ Homebrew ](https://brew.sh/) op OSX, [ Chocolade ](https://chocolatey.org/) op Vensters, of uw het pakketmanager van de distributie van Linux installeren.

Als u Linux gebruikt, moet u ervoor zorgen dat `libnss3-tools` (of het equivalent) op uw systeem is geïnstalleerd. Verdere informatie die in deze sectie van [ wordt verstrekt devcert ](https://github.com/davewasmer/devcert#skipcertutil) readme.

Sommige gebruikers hebben voorgesteld de map devcert te verwijderen om het opnieuw genereren van certificaten te starten.

* Voor MacOS-gebruikers bevindt deze map zich gewoonlijk op: `{{~/Library/Application Support/devcert }}`
* Voor Windows-gebruikers bevindt deze map zich gewoonlijk op: `${User}\AppData\Local\devcert`

## Gerelateerde lezing in onze kennisbasis voor support

* [ PWA Studio: Zelfondertekende fout van het certificaatvertrouwen ](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio: Webpack loopt vast voordat de compilatie wordt gestart](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio: browser geeft &quot;Cannot proxy to&quot;error weer](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio: validatiefouten bij het uitvoeren van de ontwikkelaarsmodus](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
