---
title: 'PWA Studio: browser kan de .local.pwadev-site niet oplossen'
description: Dit artikel biedt een oplossing voor het tijdstip waarop een ander programma of proces uw [hostbestand] (https://en.wikipedia.org/wiki/Hosts_(file\) heeft bewerkt en de vermelding voor uw projectdomein heeft verwijderd.
exl-id: a1606016-906a-433f-9e40-9faa5f9bd790
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# PWA Studio: browser kan de .local.pwadev-site niet oplossen

Dit artikel biedt een oplossing voor wanneer een ander programma of proces uw [hostbestand](https://en.wikipedia.org/wiki/Hosts_(file\)) en verwijder de ingang voor uw projectdomein.

## Betrokken producten en versies

PWA Studio voor Adobe Commerce

## Probleem

Wanneer u naar de ontwikkelings-/staging-site bladert, kunt u de `.local.pwadev` site.

## Oorzaak

Met PWA Studio kunt u een aangepaste hostnaam en een SSL-certificaat voor uw project toewijzen aan uw lokale computer. Dit betekent dat u een nieuwe vermelding maakt in het hostbestand van uw computer die er ongeveer zo uitziet `my-storefront-project-abc123.local.pwadev`.

Deze ingang vertelt om het even welke browser op de computer van de ontwikkelaar om het lokale archiefproject te bekijken wanneer het tot die URL toegang heeft. Als een ander programma of proces binnenkwam en die ingang verwijderde, zou browser niet weten waar te gaan en browser kan niet oplossen `.local.pwadev` site.

## Oplossing

U kunt [uw hostbestand handmatig bewerken](https://support.rackspace.com/how-to/modify-your-hosts-file/) om de ingang terug te voegen, maar u zou uw andere geïnstalleerde software moeten onderzoeken om te zien wat de vorige verandering heeft overschreven.

## Gerelateerde lezing in onze kennisbasis voor support

* [PWA Studio: vertrouwensfout bij niet-geautoriseerd certificaat](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio: Webpack loopt vast voordat de compilatie wordt gestart](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio: fout &quot;Cannot proxy to&quot; wordt weergegeven in browser](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio: validatiefouten bij het uitvoeren van de ontwikkelaarsmodus](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
