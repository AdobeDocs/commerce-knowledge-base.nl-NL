---
title: Exacte zoekopdracht met overeenkomst werkt niet in Adobe Commerce 2.4.x
description: Dit artikel biedt een verduidelijking voor de kwestie waarin de resultaten van zoekopdrachten op de voorgrond van de winkel met dezelfde zoektekenreeks verschillen in Adobe Commerce 2.4.x in vergelijking met Adobe Commerce 2.3.x.
exl-id: 0867558e-1d74-4b83-abf3-651ca7fc32cb
feature: Products, Search
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

<u> Eerste vereisten:</u>

Er zijn producten met kenmerkwaarden `Saga 1` en `Saga 16` in zowel Adobe Commerce 2.3- als Adobe Commerce 2.4-winkels.

<u> Stappen om te reproduceren:</u>

1. Op de opslagvoorzijde van Adobe Commerce 2.3 aangedreven opslag, ga *Saga 1* op het onderzoeksgebied in en klik **Onderzoek**.
1. In de zoekresultaten krijgt u alleen de producten met de kenmerkwaarde `Saga 1` .
1. Op de opslagvoorzijde van Adobe Commerce 2.4 aangedreven opslag, ga *Saga 1* op het onderzoeksgebied in en klik **Onderzoek**.

<u> Ware resultaat:</u>

Zoekresultaten in 2.4 omvatten producten met kenmerkwaarden `Saga 1` en `Saga 16` .

<u> Verwacht resultaat:</u>

De zoekresultaten in 2.4 zijn vergelijkbaar met die in 2.3 en omvatten alleen producten met kenmerkwaarde `Saga 1` .

## Oorzaak

De native zoekfunctionaliteit van Adobe Commerce die in 2.3.x wordt gebruikt, biedt exact overeenkomende zoekresultaten. Tijdens Live zoeken is een optionele module die beschikbaar is voor installatie en die is uitgebracht met Adobe Commerce 2.4.x anders geïmplementeerd. Het werkelijke resultaat is het verwachte gedrag wanneer de module wordt gebruikt.

## Verwante lezing

[ installeer Levende Onderzoek ](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=nl-NL) in onze gebruikersgids.

[ Levend Onderzoek ](https://experienceleague.adobe.com/nl/docs/commerce-merchant-services/live-search/overview) in onze ontwikkelaarsdocumentatie.
