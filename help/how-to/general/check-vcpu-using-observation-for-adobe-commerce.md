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

1. Klik op de startpagina van New Relic op **Apps**.
1. Klikken **Waarneming voor Adobe Commerce**.
1. De Waarneming voor de Adobe Commerce-nerdlet begint.
1. Klik op de knop **Een account selecteren** en selecteer een account.
1. U kunt de project-id, het New Relic-accountnummer of de accountnaam invullen of door de lijst met accounts bladeren.
1. Klik op het lichtblauwe vervolgkeuzemenu met het klokpictogram (naar de rechterbovenhoek van het zenuwletvenster).
1. Als u de oorzaak van een gebeurtenis/kwestie probeert te identificeren, selecteer een tijd voorafgaand aan de kaartdatum en tijd om te zien of waren er om het even welke voorafgaande gebeurtenissen/gegevens. U kunt de vooraf ingestelde tijdframes gebruiken of een aangepast tijdframe instellen door **Aangepast instellen**.
1. Klik op de tabbladen **Infra**. Er zijn drie vCPU-lijngrafieken:
   * De eerste grafiek toont **De vCPU-rijweergave duurt langer dan 2 weken (u moet een tijdlijn van meer dan 2 weken selecteren). OPMERKING: de samplefrequentie is per dag. Als de cluster upsize/downsizes op een dag voorkomt, zal de het beëindigen rijgrootte op de volgende dag worden getoond**.
   * De tweede grafiek toont **vCPU-rijweergave over tijdlijn (moet een tijdlijn groter dan 24 uur maar niet langer dan 2 weken selecteren)**.
   * De derde grafiek toont de **vCPU-rijweergave over tijdlijn DOOR NODE, bekijkt de tijdlijn MINDER dan 24 uur**.

## Gerelateerde lezing

* [Overzicht waarneming voor Adobe Commerce](/help/support-tools/observation-for-adobe-commerce/observation-adobe-commerce-overview.md) in onze kennisbasis voor ondersteuning.
