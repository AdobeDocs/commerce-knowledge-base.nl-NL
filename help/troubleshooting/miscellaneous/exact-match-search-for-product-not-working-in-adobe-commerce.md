---
title: Exacte zoekopdracht met overeenkomst werkt niet in Adobe Commerce 2.4.x
description: Dit artikel biedt een verduidelijking voor de kwestie waarin de resultaten van zoekopdrachten op de voorgrond van de winkel met dezelfde zoektekenreeks verschillen in Adobe Commerce 2.4.x in vergelijking met Adobe Commerce 2.3.x.
exl-id: 0867558e-1d74-4b83-abf3-651ca7fc32cb
feature: Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Exacte zoekopdracht met overeenkomst werkt niet in Adobe Commerce 2.4.x

Dit artikel biedt een verduidelijking voor de kwestie waarin de resultaten van zoekopdrachten op de voorgrond van de winkel met dezelfde zoektekenreeks verschillen in Adobe Commerce 2.4.x in vergelijking met Adobe Commerce 2.3.x.

## Betrokken producten en versies

- Adobe Commerce (alle implementatiemethoden) 2.4.x, 2.3.x
- Live zoeken

## Probleem

<u>Vereisten:</u>

Er zijn producten met kenmerkwaarden `Saga 1` en `Saga 16` in zowel Adobe Commerce 2.3 als Adobe Commerce 2.4 winkels.

<u>Stappen om te reproduceren:</u>

1. Voer op de winkel voor een Adobe Commerce 2.3-winkel *Saga 1* in het zoekveld en klik op **Zoeken**.
1. In zoekresultaten krijgt u alleen de producten met de kenmerkwaarde `Saga 1`.
1. Voer op de winkel voor een Adobe Commerce 2.4-winkel *Saga 1* in het zoekveld en klik op **Zoeken**.

<u>Werkelijk resultaat:</u>

Zoekresultaten in 2.4 bevatten producten met kenmerkwaarden `Saga 1` en `Saga 16`.

<u>Verwacht resultaat:</u>

De zoekresultaten in 2.4 zijn vergelijkbaar met die in 2.3 en omvatten alleen producten met kenmerkwaarde `Saga 1`.

## Oorzaak

De native zoekfunctionaliteit van Adobe Commerce die in 2.3.x wordt gebruikt, biedt exact overeenkomende zoekresultaten. Tijdens Live zoeken is een optionele module die beschikbaar is voor installatie en die is uitgebracht met Adobe Commerce 2.4.x anders geïmplementeerd. Het werkelijke resultaat is het verwachte gedrag wanneer de module wordt gebruikt.

## Verwante lezing

[Live zoeken installeren](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) in onze gebruikershandleiding.

[Live zoeken](https://devdocs.magento.com/live-search/overview.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=Live%20Search) in onze ontwikkelaarsdocumentatie.
