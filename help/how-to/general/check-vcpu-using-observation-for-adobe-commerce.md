---
title: OmgevingsvCPU-laag in uw cluster weergeven op Adobe Commerce
promoted: true
description: In dit artikel wordt uitgelegd hoe u de toewijzing van de vCPU-lagen kunt controleren met behulp van het tabblad New Relic Infra op Observation for Adobe Commerce. Waarneming voor Adobe Commerce is een New Relic-nerdlet die de status van uw Adobe Commerce-site, de huidige en de vorige tijdweergave toont.
exl-id: a0332e7e-d38d-47d3-b3da-293902f45edc
source-git-commit: 309fda5284de3b8be54e95bf2bfd8ff1777b6c90
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# OmgevingsvCPU-laag in uw cluster weergeven op Adobe Commerce

In dit artikel wordt uitgelegd hoe u de toewijzing van de vCPU-lagen kunt controleren met behulp van het tabblad New Relic Infra op Observation for Adobe Commerce. Waarneming voor Adobe Commerce is een New Relic-nerdlet die de status van uw Adobe Commerce-site, de huidige en de vorige tijdweergave toont.

## Betrokken producten en versies:

Adobe Commerce over wolkeninfrastructuur 2.4.3 - 2.4.6

## Toewijzing vCPU-niveau controleren met observatie voor Adobe Commerce:

Ga als volgt te werk om toegang te krijgen tot en u aan te melden bij de New Relic Observation for Adobe Commerce nerdlet:

1. Van de homepage van New Relic, klik **Apps**.
1. Klik **Waarneming voor Adobe Commerce**.
1. De Waarneming voor de Adobe Commerce-nerdlet begint.
1. Klik op **selecteer een rekening** dropdown en selecteer een rekening.
1. U kunt de project-id, het New Relic-accountnummer of de accountnaam invullen of door de lijst met accounts bladeren.
1. Klik op het lichtblauwe vervolgkeuzemenu met het klokpictogram (naar de rechterbovenhoek van het zenuwletvenster).
1. Als u de oorzaak van een gebeurtenis/kwestie probeert te identificeren, selecteer een tijd voorafgaand aan de kaartdatum en tijd om te zien of waren er om het even welke voorafgaande gebeurtenissen/gegevens. U kunt de vooraf ingestelde tijdkaders gebruiken of een kader van de douanetijd plaatsen door **plaats douane** te selecteren.
1. Op de lusjes klik **Infra**. Er zijn drie vCPU-lijngrafieken:
   * De eerste grafiek toont **vCPU rijmening over chronologie GREATER 2 weken (U zult een chronologie GROTER dan 2 weken moeten selecteren). OPMERKING: de samplefrequentie is per dag. Als de cluster zich op een dag upsize/downsizes voorkomt, zal de beëindigende lijstgrootte op de volgende dag** worden getoond.
   * De tweede grafiek toont **vCPU rijmening over chronologie (behoefte om een chronologie te selecteren GROTER dan 24 uur maar niet groter dan 2 weken)**.
   * De derde grafiek toont de **vCPU rijmening over chronologie DOOR NODE, zou chronologie minder dan 24 uren** moeten bekijken.

## Gerelateerde lezing

* [ Waarneming voor het overzicht van Adobe Commerce ](/help/support-tools/observation-for-adobe-commerce/observation-adobe-commerce-overview.md) in onze basis van steunkennis.
