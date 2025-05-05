---
title: Opwarmen van cache en site niet beschikbaar op Adobe Commerce
description: Dit artikel biedt een oplossing voor het opwarmen van de paginacache en er is een vastgelopen implementatie of site down.
exl-id: c91d5c1f-95e6-4240-be98-2acea49ae728
feature: Cache, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Opwarmen van cache en site niet beschikbaar op Adobe Commerce

Dit artikel biedt een oplossing voor het opwarmen van de paginacache en er is een vastgelopen implementatie of site down.

## Betrokken producten en versies

* Adobe Commerce op wolkeninfrastructuur, alle [ gesteunde versies ](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Probleem

Het geheime voorgeheugen warm op manuscript, aan het eind van de post-opstellen fase, verzendt verzoeken aan zulk een hoge tarief dat bepaalde instanties, zoals 4-cpu degenen, niet kunnen behandelen. Hun ngInx haalt het aantal werknemers op.

<u> Stappen om </u> te reproduceren:

Opwarmen van cache starten.

<u> Verwacht resultaat </u>:

Pagina&#39;s of de hele site wordt geladen.

<u> Werkelijk resultaat </u>:

De site is niet beschikbaar of de responstijd is te hoog.

## Oplossing

Beperk het aantal gelijktijdige verbindingen tijdens de cache-opwarmen. Hiervoor moet u de variabele `WARM_UP_CONCURRENCY` post-distribueren toevoegen om het aantal opwarmen aanvragen op te geven dat het opwarmen van de cache script tegelijkertijd kan verzenden. Door deze optie in te stellen, kunt u de belasting op de Adobe Commerce-cloudinfrastructuur beter beheren. Voor stappen, zie [ Post-opstellen variabelen > WARM \_UP\_CONCURRENCY ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-post-deploy#warm_up_concurrency) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

[ Volledig-Pagina Geheime voorgeheugen ](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/tools/cache-management#full-page-caching) in onze gebruikersgids
