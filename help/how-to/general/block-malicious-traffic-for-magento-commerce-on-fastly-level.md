---
title: Blokkeren van kwaadwillig verkeer voor Adobe Commerce op snelniveau
description: Dit artikel bevat de stappen die u kunt nemen om kwaadaardig verkeer te blokkeren wanneer u vermoedt dat er een DDoS-aanval plaatsvindt in uw Adobe Commerce on cloud Infrastructure Store.
exl-id: 1a834a0a-753b-432e-9c3b-ef8dd034d294
feature: Cache, Marketing Tools
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# Blokkeren van kwaadwillig verkeer voor Adobe Commerce op snelniveau

Dit artikel bevat de stappen die u kunt nemen om kwaadaardig verkeer te blokkeren wanneer u vermoedt dat er een DDoS-aanval plaatsvindt in uw Adobe Commerce on cloud Infrastructure Store.

## Betrokken producten en versies:

* Adobe Commerce op cloudinfrastructuur 2.3.x

In dit artikel veronderstellen wij dat u reeds kwaadwillige IPs en/of hun land en gebruikersagenten hebt. Adobe Commerce on cloud Infrastructure-gebruikers krijgen deze informatie doorgaans van Adobe Commerce-ondersteuning. De volgende secties verstrekken stappen voor het blokkeren van verkeer dat op deze informatie wordt gebaseerd. Alle wijzigingen moeten worden doorgevoerd in de productieomgeving.

## Toegang tot het beheerderspaneel verkrijgen

Als uw website door DDoS wordt overbelast, kunt u zich mogelijk niet aanmelden bij uw Commerce Admin (en alle stappen uitvoeren die verder in dit artikel worden beschreven).

Als u toegang tot de beheerder wilt krijgen, zet u uw website in de onderhoudsmodus, zoals beschreven in [Onderhoudsmodus in- of uitschakelen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html#instgde-cli-maint) en whitelist uw IP adres. Schakel de onderhoudsmodus uit nadat u dit hebt gedaan.

## Het verkeer van het blok door IP

Voor Adobe Commerce op de opslag van de wolkeninfrastructuur, de meest efficiënte manier om verkeer door specifieke IP adressen en subnets te blokkeren is ACL voor Fastly in Commerce Admin toe te voegen. Hier volgen de stappen met koppelingen naar meer gedetailleerde instructies:

1. Navigeer in Commerce Admin naar **Winkels** > **Configuratie** > **Geavanceerd** > **Systeem** > **Volledige paginacache** > **Snelle configuratie**.
1. [Creeer nieuwe ACL](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/ACL.md) met een lijst van IP adressen of subnets u gaat blokkeren.
1. Voeg het aan de ACL lijst en het blok toe zoals die in [Blokkeren](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) handleiding voor de module Fastly\_Cdn voor Adobe Commerce.

## Blokverkeer per land

Voor de Adobe Commerce op de opslag van de wolkeninfrastructuur, is de meest efficiënte manier om verkeer door land(en) te blokkeren toevoegen ACL voor Fastly in de Admin van Commerce.

1. Navigeer in Commerce Admin naar **Winkels** > **Configuratie** > **Geavanceerd** > **Systeem** > **Volledige paginacache** > **Snelle configuratie**.
1. Selecteer de landen en vorm het blokkeren gebruikend ACL zoals die in wordt beschreven [Blokkeren](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) handleiding voor de module Fastly\_Cdn voor Adobe Commerce.

## Het verkeer van het blok door gebruikersagent

Om het blokkeren te vestigen die op gebruikersagent wordt gebaseerd, moet u een fragment van douaneVCL aan uw Snelle configuratie toevoegen. Voer hiertoe de volgende stappen uit:

1. Navigeer in Commerce Admin naar **Winkels** > **Configuratie** > **Geavanceerd** > **Systeem** > **Volledige paginacache**.
1. Vervolgens **Snelle configuratie** > **Aangepaste VCL-fragmenten**.
1. Maak het nieuwe aangepaste fragment dat wordt beschreven in het dialoogvenster [Aangepaste VCL-fragmenten](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/CUSTOM-VCL-SNIPPETS.md) handleiding voor de module Snelheid\_Cdn. U kunt het volgende codevoorbeeld als voorbeeld gebruiken. Deze steekproef maakt verkeer voor de steekproef onbruikbaar `AhrefsBot` en `SemrushBot` gebruikersagenten.

```php
name: block_bad_useragents
  type: recv
  priority: 5
  VCL:
  if ( req.http.User-Agent ~ "(AhrefsBot|SemrushBot)" ) {
      error 405 "Not allowed";
  }
```

## Snelheidsbeperking (experimentele snelfunctionaliteit)

Er is een experimentele snelfunctionaliteit voor Adobe Commerce op cloudinfrastructuur waarmee u de maximale snelheid voor bepaalde paden en kruippaden kunt opgeven. Verwijs naar de [Documentatie van de module Snel](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/RATE-LIMITING.md) voor meer informatie.

De functionaliteit moet uitgebreid op het opvoeren worden getest, alvorens op productie wordt gebruikt, omdat het wettig verkeer zou kunnen blokkeren.

## Aanbevolen: het bijwerken van robots.txt overwegen

Uw `robots.txt` bepaalde zoekmachines, crawlers en robots bepaalde pagina&#39;s niet laten kruipen. De voorbeelden van pagina&#39;s die niet zouden moeten worden gekropen zijn de pagina&#39;s van het onderzoeksresultaat, controle, klanteninformatie etc. Als u robots niet door deze pagina&#39;s laat kruipen, kunt u het aantal aanvragen dat door deze robots wordt gegenereerd, verminderen.

Er zijn twee belangrijke overwegingen wanneer u `robots.txt`:

* Robots kunnen uw `robots.txt`. Vooral malware-robots, die het web scannen op kwetsbaarheden op het gebied van beveiliging, en e-mailadressen die door spammers worden gebruikt, zullen geen aandacht besteden.
* De `robots.txt` bestand is een openbaar beschikbaar bestand. Iedereen kan zien welke gedeelten van uw server u niet wilt gebruiken voor robots.

De basisinformatie en standaard Adobe Commerce `robots.txt` kan worden gevonden in [Zoekmachinekrobots](https://docs.magento.com/m2/ee/user_guide/marketing/search-engine-robots.html) artikel in onze ontwikkelaarsdocumentatie.

Voor algemene informatie en aanbevelingen over `robots.txt`, zie:

* [Een robots.txt maken](https://developers.google.com/search/docs/advanced/robots/create-robots-txt) bestand van Google Support
* [Info /robots.txt](https://www.robotstxt.org/robotstxt.html) door robotstxt.org

Werk met uw ontwikkelaar en/of SEO-expert om te bepalen welke Gebruikersagenten u wilt toestaan of welke u wilt weigeren.

## Verwante lezing

[Productspecifieke licentievoorwaarden voor Adobe Commerce op Cloud](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/PSLT-AdobeCommerceCloud-WW-2023v1.pdf)
