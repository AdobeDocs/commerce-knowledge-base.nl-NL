---
title: Implementatiedowntime in Adobe Commerce op cloudinfrastructuur verminderen
description: Adobe Commerce on cloud Infrastructure biedt de functie **Configuration Management** om de downtime van het onderhoud aanzienlijk te verminderen en een efficiënte configuratie van uw winkel in verschillende omgevingen te bieden. Voor Adobe Commerce op cloudinfrastructuur 2.2.x en latere implementaties ondersteunt deze functie concepten en opties voor de implementatie van de pijplijn met beperkte stappen.
exl-id: fde3571c-d95c-4a9b-a024-3b29f9c491ab
feature: Build, Cloud, Configuration, Deploy
source-git-commit: 23d957ceac17f9989d14b215582304199d398545
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Implementatiedowntime in Adobe Commerce op cloudinfrastructuur verminderen

Adobe Commerce op de cloudinfrastructuur biedt de **Configuratiebeheer** gebruiken. Voor Adobe Commerce op cloudinfrastructuur 2.2.x en latere implementaties ondersteunt deze functie concepten en opties voor de implementatie van de pijplijn met beperkte stappen.

## Overzicht

De pijnlijke en tijdrovende problemen bij de implementatie van uw webwinkel zijn onder andere:

* **Dezelfde configuratie toepassen in alle omgevingen.** Normaal, zou u configuraties manueel of door gecompliceerde gegevensbestandupdates ingaan. Met het Beheer van de Configuratie, voert u configuraties van het gegevensbestand in één enkel dossier uit om het met uw code van uw lokale ontwikkelomgeving aan Integratie, het Opvoeren, en Productie later te duwen.

* **Sitedowntime bij het implementeren van statische inhoud.** Statische inhoud wordt doorgaans geïmplementeerd tijdens de [implementatiefase](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase). Dit kan tot 30 minuten of meer duren, wat niet aanvaardbaar is voor het bedrijfsleven. Het Beheer van de configuratie verplaatst statische inhoudsplaatsing aan [bouwfase](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase), waarvoor geen downtime is vereist.

## Technologieversies

* Adobe Commerce over cloudinfrastructuur **2.1.4.** en later voor configuratiebeheer
* Adobe Commerce over cloudinfrastructuur **2,2** en later voor Configuration Management/Pipeline Deployment

## Wat is configuratiebeheer?

Om een lang verhaal kort te maken, haalt het proces van het Beheer van de Configuratie (ook genoemd de Plaatsing van de Pijpleiding) alle configuratiemontages van uw Adobe Commerce op de implementatie van de wolkeninfrastructuur (gegevensbestand) in één enkel PHP dossier uit. Vervolgens voegt u het bestand toe aan de Git-instelling en duwt u het in al uw omgevingen.

Dit biedt de volgende voordelen:

* **Consistente instellingen in alle omgevingen:** alle instellingen die naar het configuratiebestand worden geëxporteerd, worden vergrendeld (de corresponderende velden in de Commerce-beheerder worden alleen-lezen). Dit zorgt voor consistente configuraties wanneer u het bestand in al uw omgevingen plaatst.
* **Minder downtime:** de statische dossierplaatsing verschuift van [implementatiefase](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase) (waarvoor de locatie in de onderhoudsmodus moet staan) naar de [bouwfase](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase) (wanneer de locatie niet in de modus Onderhoud staat en niet wordt uitgepakt in geval van fouten of problemen).
* **Beschermde vertrouwelijke gegevens:** met Adobe Commerce op cloudinfrastructuur 2.2 en hoger exporteert het proces ook gevoelige gegevens (bijvoorbeeld gegevens van betaalgateway) naar de `env.php` bestand. Dit bestand moet alleen worden opgeslagen in de omgeving waarin het is gemaakt en niet worden geduwd met de Git-vertakkingen.

Wij adviseren sterk het toepassen van de benadering van het Beheer van de Configuratie in uw plaatsing.

## Configuratiebeheer in onze documentatie voor ontwikkelaars

* [Configuratiebeheer voor **2.1.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) en de [voorbeeld](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) in de *Adobe Commerce on cloud Infrastructure Guide*
* [Configuratiebeheer voor **2.2.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) en de [voorbeeld](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) in de *Adobe Commerce on cloud Infrastructure Guide*
* [Upgrade uitvoeren vanaf 2.0.X of 2.1.X](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html#upgrade-from-older-versions) van de *Adobe Commerce upgraden op cloudinfrastructuur* onderwerp
* [Implementatie van pijpleidingen](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/overview.html) in de *Adobe Commerce on cloud Infrastructure Configuration Guide* - Voor Adobe Commerce op cloudinfrastructuur hoeft u de instructies in deze handleiding niet te volgen. De inhoud is uitsluitend ter referentie. We bieden Adobe Commerce al aan de build-server, integratieomgevingen en meer op cloudinfrastructuur.
