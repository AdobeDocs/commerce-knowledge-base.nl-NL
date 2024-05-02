---
title: Opwarmen van cache en site niet beschikbaar op Adobe Commerce
description: Dit artikel biedt een oplossing voor het opwarmen van de paginacache en er is een vastgelopen implementatie of site down.
exl-id: c91d5c1f-95e6-4240-be98-2acea49ae728
feature: Cache, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Opwarmen van cache en site niet beschikbaar op Adobe Commerce

Dit artikel biedt een oplossing voor het opwarmen van de paginacache en er is een vastgelopen implementatie of site down.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, alle [ondersteunde versies](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Probleem

Het geheime voorgeheugen warm op manuscript, aan het eind van de post-opstellen fase, verzendt verzoeken aan zulk een hoge tarief dat bepaalde instanties, zoals 4-cpu degenen, niet kunnen behandelen. Hun ngInx haalt het aantal werknemers op.

<u>Stappen om te reproduceren</u>:

Opwarmen van cache starten.

<u>Verwacht resultaat</u>:

Pagina&#39;s of de hele site wordt geladen.

<u>Werkelijk resultaat</u>:

De site is niet beschikbaar of de responstijd is te hoog.

## Oplossing

Beperk het aantal gelijktijdige verbindingen tijdens de cache-opwarmen. Hiervoor moet u de opdracht `WARM_UP_CONCURRENCY` post-opstellen variabele om het aantal warm-op verzoeken te specificeren dat het geheim voorgeheugenwarm-up manuscript kan gelijktijdig verzenden. Door deze optie in te stellen, kunt u de belasting op de Adobe Commerce-cloudinfrastructuur beter beheren. Zie voor stappen [Variabelen na implementatie > WARM\_UP\_CONCURRENCY](https://devdocs.magento.com/cloud/env/variables-post-deploy.html#warm_up_concurrency) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

[Cache van volledige pagina](https://docs.magento.com/user-guide/system/cache-full-page.html) in onze gebruikershandleiding
