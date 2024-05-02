---
title: 'PWA Studio: validatiefouten bij het uitvoeren van de ontwikkelaarsmodus'
description: Dit onderwerp bespreekt een oplossing voor wanneer de bevestigingsfouten voorkomen wanneer het runnen van ontwikkelaarswijze in Progressieve Studio van de Web App (PWA) voor Adobe Commerce als resultaat van eerder niet creërend venia-concept (Venia is een PWA storefront.) omgevingsbestand. Dit bestand bevat de variabelen voor uw lokale ontwikkelomgeving.
exl-id: 97d042ef-88e6-4eda-a834-2cff4de276e2
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# PWA Studio: validatiefouten bij het uitvoeren van de ontwikkelaarsmodus

Dit onderwerp bespreekt een oplossing voor wanneer de bevestigingsfouten voorkomen wanneer het runnen van ontwikkelaarswijze in Progressieve Studio van de Web App (PWA) voor Adobe Commerce als resultaat van eerder niet creërend venia-concept (Venia is een PWA storefront.) omgevingsbestand. Dit bestand bevat de variabelen voor uw lokale ontwikkelomgeving.

## Betrokken producten en versies

* PWA Studio voor Adobe Commerce

## Probleem

<u>Stap om te reproduceren</u>:

* Voer de ontwikkelaarsmodus uit in PWA Studio voor Adobe Commerce.

<u>Verwacht resultaat</u>:

* De server van de PWA Studio begint normaal.

<u>Werkelijk resultaat</u>:

* U ziet validatiefouten, die er ongeveer als volgt kunnen uitzien:

```
    ⓧ  Missing required environment variables:         MAGENTO_BACKEND_URL: Connect to an instance of Adobe Commerce 2.3 by specifying its public domain name. (eg.         "https://master-7rqtwti-mfwmkrjfqvbjk.us-4.magentosite.cloud/")      ⚠  No .env file in ./packages/venia-concept. Autogenerate a .env file by running the command 'buildpack         create-env-file ./packages/venia-concept'.
```

## Oorzaak

Het bestand met omgevingsvariabelen voor uw lokale ontwikkelomgeving ontbreekt. Het bestand dat met de onderstaande opdracht wordt gegenereerd, bevat de variabelen voor uw lokale ontwikkelomgeving.

## Oplossing

Controleer of u de opdracht uitvoert

```
npx @magento/pwa-buildpack create-env-file packages/venia-concept
```

in de hoofdmap om het bestand te genereren dat de variabelen voor uw lokale ontwikkelomgeving bevat.

## Gerelateerde lezing

* [PWA Studio voor Adobe Commerce-documentatie](https://magento.github.io/pwa-studio/)
* [Venia Storefront (concept)](https://magento.github.io/pwa-studio/venia-pwa-concept/)
