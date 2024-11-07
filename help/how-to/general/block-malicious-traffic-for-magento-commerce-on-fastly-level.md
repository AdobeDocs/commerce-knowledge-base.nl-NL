---
title: Blokkeren van kwaadwillig verkeer voor Adobe Commerce op snelniveau
description: Dit artikel bevat de stappen die u kunt nemen om kwaadaardig verkeer te blokkeren wanneer u vermoedt dat er een DDoS-aanval plaatsvindt in uw Adobe Commerce on cloud Infrastructure Store.
exl-id: 1a834a0a-753b-432e-9c3b-ef8dd034d294
feature: Cache, Marketing Tools
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Om toegang tot Admin te krijgen, zet uw website in onderhoudswijze zoals die in [ wordt beschreven laat of maakt onderhoudswijze ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) toe onbruikbaar en whitelist uw IP adres. Schakel de onderhoudsmodus uit nadat u dit hebt gedaan.

## Het verkeer van het blok door IP

Voor Adobe Commerce op de opslag van de wolkeninfrastructuur, de meest efficiënte manier om verkeer door specifieke IP adressen en subnets te blokkeren is ACL voor Fastly in Commerce Admin toe te voegen. Hier volgen de stappen met koppelingen naar meer gedetailleerde instructies:

1. In Commerce Admin, navigeer aan **Opslag** > **Configuratie** > **Geavanceerd** > **Systeem** > **Volledige het Geheime voorgeheugen van de Pagina** > **Snelle Configuratie**.
1. [ creeer nieuwe ACL ](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/ACL.md) met een lijst van IP adressen of subnets u gaat blokkeren.
1. Voeg het aan de ACL lijst en het blok toe zoals die in de [ Blocking ](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) gids voor de Fastly \_Cdn module voor Adobe Commerce wordt beschreven.

## Blokverkeer per land

Voor de Adobe Commerce op de opslag van de wolkeninfrastructuur, is de meest efficiënte manier om verkeer door land(en) te blokkeren toevoegen ACL voor Fastly in de Admin van Commerce.

1. In Commerce Admin, navigeer aan **Opslag** > **Configuratie** > **Geavanceerd** > **Systeem** > **Volledige het Geheime voorgeheugen van de Pagina** > **Snelle Configuratie**.
1. Selecteer de landen en vorm het blokkeren gebruikend ACL zoals die in de [ Blocking ](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) gids voor de Fastly \_Cdn module voor Adobe Commerce wordt beschreven.

## Het verkeer van het blok door gebruikersagent

Om het blokkeren te vestigen die op gebruikersagent wordt gebaseerd, moet u een fragment van douaneVCL aan uw Snelle configuratie toevoegen. Voer hiertoe de volgende stappen uit:

1. In Commerce Admin, navigeer aan **Opslag** > **Configuratie** > **Geavanceerd** > **Systeem** > **het Volledige Geheime voorgeheugen van de Pagina**.
1. Dan **snel configuratie** > **de Fragmenten van de Douane VCL**.
1. Creeer het nieuwe douanefragment zoals die in de [ de fragmenten van de Douane VCL ](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/CUSTOM-VCL-SNIPPETS.md) gids voor de Fastly \_Cdn module wordt beschreven. U kunt het volgende codevoorbeeld als voorbeeld gebruiken. In dit voorbeeld wordt het verkeer voor de gebruikersagents `AhrefsBot` en `SemrushBot` uitgeschakeld.

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

Er is een experimentele snelfunctionaliteit voor Adobe Commerce op cloudinfrastructuur waarmee u de maximale snelheid voor bepaalde paden en kruippaden kunt opgeven. Gelieve te verwijzen de [ documentatie van de module van de Snelheid ](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/RATE-LIMITING.md) voor details.

De functionaliteit moet uitgebreid op het opvoeren worden getest, alvorens op productie wordt gebruikt, omdat het wettig verkeer zou kunnen blokkeren.

## Aanbevolen: het bijwerken van robots.txt overwegen

Als u het `robots.txt` -bestand bijwerkt, blijven bepaalde zoekprogramma&#39;s, crawlers en robots op bepaalde pagina&#39;s wellicht niet horizontaal schuiven. De voorbeelden van pagina&#39;s die niet zouden moeten worden gekropen zijn de pagina&#39;s van het onderzoeksresultaat, controle, klanteninformatie etc. Als u robots niet door deze pagina&#39;s laat kruipen, kunt u het aantal aanvragen dat door deze robots wordt gegenereerd, verminderen.

Er zijn twee belangrijke overwegingen wanneer u `robots.txt` gebruikt:

* Robots kunnen uw `robots.txt` negeren. Vooral malware-robots, die het web scannen op kwetsbaarheden op het gebied van beveiliging, en e-mailadressen die door spammers worden gebruikt, zullen geen aandacht besteden.
* Het bestand `robots.txt` is een openbaar beschikbaar bestand. Iedereen kan zien welke gedeelten van uw server u niet wilt gebruiken voor robots.

De basisinformatie en standaardAdobe Commerce `robots.txt` configuratie kunnen in het [ artikel van de Motor van het Onderzoek van de Motor Robots ](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/seo-overview#search-engine-robots) in onze ontwikkelaarsdocumentatie worden gevonden.

Zie voor algemene informatie en aanbevelingen over `robots.txt`:

* [ creeer een robots.txt ](https://developers.google.com/search/docs/advanced/robots/create-robots-txt) dossier door de Steun van Google
* [ Ongeveer /robots.txt](https://www.robotstxt.org/robotstxt.html) door robotstxt.org

Werk met uw ontwikkelaar en/of SEO-expert om te bepalen welke Gebruikersagenten u wilt toestaan of welke u wilt weigeren.

## Verwante lezing

[ Product-Specifieke het Vergunningstermijnen voor Adobe Commerce op Wolk ](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/PSLT-AdobeCommerceCloud-WW-2023v1.pdf)
