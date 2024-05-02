---
title: Tips voor tests van andere bedrijven voor Adobe Commerce op cloudinfrastructuur
description: Dit artikel bevat opties voor het delen van toegang met derden voor tests/validatie wanneer u een probleem hebt met een extensie voor Adobe Commerce op cloudinfrastructuur.
exl-id: e2d80aa9-8b68-48ed-bec5-68e128611a1e
feature: Best Practices, Cloud
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Tips voor tests van andere bedrijven voor Adobe Commerce op cloudinfrastructuur

Dit artikel bevat opties voor het delen van toegang met derden voor tests/validatie wanneer u een probleem hebt met een extensie voor Adobe Commerce op cloudinfrastructuur.
De juiste interne procedures en vereisten voor gegevensbeveiliging moeten van uw kant worden gevolgd wanneer u besluit hoe toegang kan worden verleend aan derden.

## Betrokken producten en versies:

* Adobe Commerce over cloudinfrastructuur 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.3

## Welke omgevingen worden gebruikt voor tests

Afhankelijk van uw interne veiligheidsnormen, kunt u verkiezen om de derdeproblemen op een lokale milieu te hebben problemen oplossen. Als het probleem niet lokaal kan worden gereproduceerd, kunt u toegang tot uw cloud-omgeving bieden. Als u ervoor kiest dit te doen, moet u ervoor zorgen dat u zich aan uw interne beveiligingsnormen houdt. Als u toegang biedt tot een van uw cloudomgevingen, moet u ervoor zorgen dat uw externe partij duidelijk is wat u kunt doen en welke goedkeuring is vereist voor zaken zoals alleen replicatie of het toestaan van wijzigingen in de code. Dit is met name belangrijk voor productieomgevingen.

## Toegang en gegevens aan derden verstrekken

* Geef uw externe leverancier toegang tot de cloudomgeving. Verwante artikelen:

   * [Adobe Commerce Help Center - Gebruikershandleiding > GEDEELDE TOEGANG: ANDERE GEBRUIKERS KRIJGEN TOEGANG TOT UW ACCOUNT](/help/help-center-guide/help-center/magento-help-center-user-guide.md#shared-access) in onze kennisbasis voor ondersteuning.
   * [Uw Commerce-account delen](https://docs.magento.com/user-guide/magento/magento-account-share.html) in onze gebruikershandleiding.

* Creeer een gegevensbestandstortplaats (of geef de derdeverkoper toegang om dit te doen). Dit kan worden gedaan met de CLI of in de Commerce Admin. Deze stortplaats van DB zal klantengegevens verduisteren, zodat alles zij code en product SKU&#39;s, enz. krijgen, geen merkgebonden/klantengegevens. Ter referentie, gebruik [Uw Commerce-account delen] (/help/how-to/general/create-database-dump-on-cloud.md) in onze kennisbasis voor ondersteuning.
* Nadat het testen is voltooid, moet u de gedeelde toegang tot uw cloudomgeving intrekken, zoals beschreven in [Adobe Commerce Help Center Handboek > Gedeelde toegang intrekken](/help/help-center-guide/help-center/magento-help-center-user-guide.md#revoke-shared-access) in onze kennisbasis voor ondersteuning.

## Testen van beste praktijken

De standaardpraktijk moet op een lokaal milieu problemen oplossen. Ga naar Staging als het probleem niet lokaal kan worden gereproduceerd. De derde moet mogelijk de productie controleren. Zorg ervoor dat uw derde zich ervan bewust is dat zij slechts proberen om de kwestie op Productie en het Opvoeren te reproduceren en geen codeveranderingen aan te brengen, en als zij code moeten aanbrengen verandert, moeten zij eerst uw toestemming krijgen.

## Gerelateerde lezing

* [Aanbevolen procedures voor het gebruik van extensies van derden in Adobe Commerce](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento) in onze kennisbasis voor ondersteuning.
