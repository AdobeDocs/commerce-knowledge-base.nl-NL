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

Om onderhoud onderbreking drastisch te verminderen en efficiënte configuratie van uw opslag over milieu&#39;s te verstrekken, verstrekt Adobe Commerce op wolkeninfrastructuur de **eigenschap van het Beheer van de Configuratie 0} {.** Voor Adobe Commerce op cloudinfrastructuur 2.2.x en latere implementaties ondersteunt deze functie concepten en opties voor de implementatie van de pijplijn met beperkte stappen.

## Overzicht

De pijnlijke en tijdrovende problemen bij de implementatie van uw webwinkel zijn onder andere:

* **Toepassend de zelfde configuratie over alle milieu&#39;s.** Doorgaans voert u handmatig configuraties in of via gecompliceerde database-updates. Met het Beheer van de Configuratie, voert u configuraties van het gegevensbestand in één enkel dossier uit om het met uw code van uw lokale ontwikkelomgeving aan Integratie, het Opvoeren, en Productie later te duwen.

* **de onderbreking van de Plaats wanneer het opstellen van statische inhoud.** Typisch, wordt de statische inhoud opgesteld tijdens [ opstellen fase ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase). Dit kan tot 30 minuten of meer duren, wat niet aanvaardbaar is voor het bedrijfsleven. Het Beheer van de configuratie verplaatst statische inhoudsplaatsing aan [ bouwt fase ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase), die geen onderbreking vereist.

## Technologieversies

* Adobe Commerce op wolkeninfrastructuur **2.1.4** en later voor het Beheer van de Configuratie
* Adobe Commerce op wolkeninfrastructuur **2.2** en later voor het Beheer van de Configuratie/de Plaatsing van de Pijpleiding

## Wat is configuratiebeheer?

Om een lang verhaal kort te maken, haalt het proces van het Beheer van de Configuratie (ook genoemd de Plaatsing van de Pijpleiding) alle configuratiemontages van uw Adobe Commerce op de implementatie van de wolkeninfrastructuur (gegevensbestand) in één enkel PHP dossier uit. Vervolgens voegt u het bestand toe aan de Git-instelling en duwt u het in al uw omgevingen.

Dit biedt de volgende voordelen:

* **Consistente montages in alle milieu&#39;s:** om het even welke montages die worden uitgevoerd naar het configuratiedossier worden gesloten (de overeenkomstige gebieden in Commerce worden Admin read-only), die verenigbare configuraties verzekert aangezien u het dossier over al uw milieu&#39;s duwt.
* **Verminderde onderbreking:** de statische verschuivingen van de dossierplaatsing van [ opstellen fase ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase) (die de plaats om op de wijze van het Onderhoud vereist te zijn) aan [ bouwt fase ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase) (wanneer de plaats niet op de wijze van het Onderhoud is en niet zal worden onderdrukt als de fouten of de kwesties) voorkomen.
* **Beschermde gevoelige gegevens:** met Adobe Commerce op wolkeninfrastructuur 2.2 en recenter, voert het proces ook om het even welke gevoelige gegevens (bijvoorbeeld, geloofsbrieven van de betalingsgateway) naar het `env.php` dossier uit. Dit bestand moet alleen worden opgeslagen in de omgeving waarin het is gemaakt en niet worden geduwd met de Git-vertakkingen.

Wij adviseren sterk het toepassen van de benadering van het Beheer van de Configuratie in uw plaatsing.

## Configuratiebeheer in onze documentatie voor ontwikkelaars

* [ beheer van de Configuratie voor **2.1.X** ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) en het [ voorbeeld ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) in *Adobe Commerce op de Gids van de wolkeninfrastructuur*
* [ beheer van de Configuratie voor **2.2.X** ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) en het [ voorbeeld ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) in *Adobe Commerce op de Gids van de wolkeninfrastructuur*
* [ Verbetering van 2.0.X of 2.1.X ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html#upgrade-from-older-versions) sectie van de *Verbetering Adobe Commerce op het onderwerp van de wolkeninfrastructuur*
* [ Plaatsing van de Pijpleiding ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/overview.html) in *Adobe Commerce op de Gids van de Configuratie van de wolkeninfrastructuur* - voor Adobe Commerce op wolkeninfrastructuur, te hoeven u niet om de instructies in deze gids te volgen. De inhoud is uitsluitend ter referentie. We bieden Adobe Commerce al aan de build-server, integratieomgevingen en meer op cloudinfrastructuur.
