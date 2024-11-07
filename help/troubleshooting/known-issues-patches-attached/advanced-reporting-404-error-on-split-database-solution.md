---
title: Advanced Reporting 404-fout bij gesplitste databaseoplossing
description: Dit artikel biedt een patch voor Adobe Commerce 2.3.x-gebruikers met de [gesplitste databaseoplossing](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master) die een fout van 404 ervaren wanneer ze proberen Geavanceerde rapportage te gebruiken.
exl-id: b81d4ada-5f38-4882-bc5b-ab4ccd63fc5f
feature: Commerce Intelligence
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Advanced Reporting 404-fout bij gesplitste databaseoplossing

Dit artikel verstrekt een flard voor Adobe Commerce 2.3.x gebruikers met de [ gespleten gegevensbestandoplossing ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master) die een fout 404 wanneer het proberen om Geavanceerde Rapportering te gebruiken ervaart.

## Betrokken producten en versies

Adobe Commerce 2.3.0 - 2.3.5-p1

## Probleem

De patch verhelpt het probleem waarbij de onjuiste verbindingsnaam wordt gebruikt om aanhalingsgegevens te verzamelen. Omdat de verkeerde verbindingsnaam wordt gebruikt, worden de citaatgegevens niet verzonden naar Magento Business Intelligence (MBI) en de rapporten kunnen niet worden geproduceerd.

## Oplossing

Pas het [ flard ](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip) toe dat in dit artikel wordt verstrekt.

## Reparatie

De patch is aan dit artikel gekoppeld. Klik op de volgende koppeling om deze te downloaden:

[MDVA-26831\_EE\_2.3.4\_v1.composer.patch](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip)

## Hoe de pleister aanbrengen

Pak het dossier uit en volg de instructies in [ hoe te om een composerflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) wordt verstrekt.
