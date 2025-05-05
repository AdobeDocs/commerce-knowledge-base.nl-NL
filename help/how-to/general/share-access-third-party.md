---
title: Tips voor tests van andere bedrijven voor Adobe Commerce op cloudinfrastructuur
description: Dit artikel bevat opties voor het delen van toegang met derden voor tests/validatie wanneer u een probleem hebt met een extensie voor Adobe Commerce op cloudinfrastructuur.
exl-id: e2d80aa9-8b68-48ed-bec5-68e128611a1e
feature: Best Practices, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

   * [ de Gids van de Gebruiker van het Centrum van de Hulp van Adobe Commerce > GEDEELDE TOEGANG: DE VOORRECHTEN VAN DE VERLENER VOOR ANDERE GEBRUIKERS OM TOT UW ACCOUNT ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#shared-access) in onze steun kennisbasis toegang te hebben.
   * [ delend Uw Rekening van Commerce ](https://experienceleague.adobe.com/nl/docs/commerce-admin/start/commerce-account/commerce-account-share) in onze gebruikersgids.

* Creeer een gegevensbestandstortplaats (of geef de derdeverkoper toegang om dit te doen). Dit kan worden gedaan met de CLI of in de Commerce Admin. Deze stortplaats van DB zal klantengegevens verduisteren, zodat alles zij code en product SKU&#39;s, enz. krijgen, geen merkgebonden/klantengegevens. Voor verwijzing, gebruik [ delend Uw Rekening van Commerce ] (/help/how-to/general/create-database-dump-on-cloud.md) in onze steun kennisbasis.
* Zodra het testen volledig is, zorg ervoor om de gedeelde toegang tot uw wolkenmilieu, zoals die in [ wordt beschreven de Gids van de Gebruiker van het Centrum van de Hulp van Adobe Commerce > Intrekken (schrapt gedeelde toegang) ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#revoke-shared-access) in onze basis van steunkennis.

## Testen van beste praktijken

De standaardpraktijk moet op een lokaal milieu problemen oplossen. Ga naar Staging als het probleem niet lokaal kan worden gereproduceerd. De derde moet mogelijk de productie controleren. Zorg ervoor dat uw derde zich ervan bewust is dat zij slechts proberen om de kwestie op Productie en het Opvoeren te reproduceren en geen codeveranderingen aan te brengen, en als zij code moeten aanbrengen verandert, moeten zij eerst uw toestemming krijgen.

## Gerelateerde lezing

* [ Beste praktijken voor het gebruiken van derdeuitbreidingen in Adobe Commerce ](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento) in onze basis van de steunkennis.
