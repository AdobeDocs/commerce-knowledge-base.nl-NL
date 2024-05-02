---
title: Advanced Reporting 404-fout bij gesplitste databaseoplossing
description: Dit artikel biedt een patch voor Adobe Commerce 2.3.x-gebruikers met de [gesplitste databaseoplossing](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master.html) die een fout van 404 ervaren wanneer ze proberen Geavanceerde rapportage te gebruiken.
exl-id: b81d4ada-5f38-4882-bc5b-ab4ccd63fc5f
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Advanced Reporting 404-fout bij gesplitste databaseoplossing

Dit artikel bevat een patch voor Adobe Commerce 2.3.x-gebruikers met de [gesplitste databaseoplossing](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master.html) die een fout 404 ervaren wanneer het proberen om Geavanceerde Rapportering te gebruiken.

## Betrokken producten en versies

Adobe Commerce 2.3.0 - 2.3.5-p1

## Probleem

De patch verhelpt het probleem waarbij de onjuiste verbindingsnaam wordt gebruikt om aanhalingsgegevens te verzamelen. Omdat de verkeerde verbindingsnaam wordt gebruikt, worden de citaatgegevens niet verzonden naar Magento Business Intelligence (MBI) en de rapporten kunnen niet worden geproduceerd.

## Oplossing

Pas de [pleister](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip) in dit artikel.

## Reparatie

De patch is aan dit artikel gekoppeld. Klik op de volgende koppeling om deze te downloaden:

[MDVA-26831\_EE\_2.3.4\_v1.composer.patch](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip)

## Hoe de pleister aanbrengen

Pak het bestand uit en volg de instructies in [Hoe een door Adobe geleverde componentpleister aanbrengen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).
