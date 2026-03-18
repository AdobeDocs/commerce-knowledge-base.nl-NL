---
title: 'PWA Studio: Validatiefouten bij uitvoering van ontwikkelaarsmodus'
description: Dit onderwerp bespreekt een oplossing voor wanneer de bevestigingsfouten voorkomen wanneer het runnen van ontwikkelaarwijze in Progressieve Studio van de Web App (PWA) voor Adobe Commerce als resultaat van eerder het venia-concept (Venia is een PWA storefront.) milieudossier. Dit bestand bevat de variabelen voor uw lokale ontwikkelomgeving.
exl-id: 97d042ef-88e6-4eda-a834-2cff4de276e2
feature: Configuration
role: Developer
source-git-commit: 9d32a5971341ed8dc46e0932c10eaac4d17ec299
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# PWA Studio: Validatiefouten bij uitvoering van ontwikkelaarsmodus

Dit onderwerp bespreekt een oplossing voor wanneer de bevestigingsfouten voorkomen wanneer het runnen van ontwikkelaarwijze in Progressieve Studio van de Web App (PWA) voor Adobe Commerce als resultaat van eerder het venia-concept (Venia is een PWA storefront.) milieudossier. Dit bestand bevat de variabelen voor uw lokale ontwikkelomgeving.

## Betrokken producten en versies

* PWA Studio voor Adobe Commerce

## Probleem

<u> Stap om te reproduceren </u>:

* Voer de ontwikkelaarsmodus uit in PWA Studio for Adobe Commerce.

<u> Verwacht resultaat </u>:

* De PWA Studio-server wordt normaal gestart.

<u> Werkelijk resultaat </u>:

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

* [ PWA Studio voor de Documentatie van Adobe Commerce ](https://developer.adobe.com/commerce/pwa-studio/)
* [ Venia Storefront (Concept) ](https://developer.adobe.com/commerce/pwa-studio/guides/packages/venia/)
