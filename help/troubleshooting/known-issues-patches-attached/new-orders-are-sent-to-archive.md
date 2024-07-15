---
title: Nieuwe bestellingen worden naar archief verzonden
description: Dit artikel bevat een patch voor het bekende Adobe Commerce 2.2.0-probleem met betrekking tot de nieuwe bestellingen die worden weergegeven in het archief in plaats van het orderraster in Commerce Admin.
exl-id: 37b70d28-0569-44f2-b677-29b2bde0bc5c
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Nieuwe bestellingen worden naar archief verzonden

Dit artikel bevat een patch voor het bekende Adobe Commerce 2.2.0-probleem met betrekking tot de nieuwe bestellingen die worden weergegeven in het archief in plaats van het orderraster in Commerce Admin.

>[!NOTE]
>
>Het probleem is opgelost in 2.2.3 en hoger.

## Probleem

Wanneer klanten bestellingen plaatsen, worden deze weergegeven in het raster voor gearchiveerde bestellingen in plaats van in het gewone raster voor bestellingen.

<u> Stappen om </u> te reproduceren:

1. Voeg een product toe aan de winkelwagentje, ga door het afrekenen en plaats de bestelling.
1. In Commerce Admin, navigeer aan **Verkoop** > **Verrichtingen** > **Orde**. Zie de volgorde in het raster.
1. Navigeer aan **Verkoop** > **Archief** > **Orden**. Zie de nieuwe volgorde in het raster.

<u> Verwachte resultaten </u>:

De volgorde wordt alleen weergegeven in het raster Orden.

<u> Ware resultaten </u>:

De volgorde wordt weergegeven in het raster Orden en in het archiefraster van de volgorde.

## Oplossing

Nadat u de patch hebt toegepast, worden de bestellingen op de verwachte wijze weergegeven in het raster Volgorde. Maar u moet in Commerce Admin manueel herstellen degenen die naar archief werden verzonden alvorens de flard werd toegepast.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[Download MDVA-8007\_EE\_2.2.0\_v1.composer.patch](assets/MDVA-8007_EE_2.2.0_v1.composer.patch.zip)

### Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce 2.2.0

De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce op locatie, Adobe Commerce op cloudinfrastructuur 2.2.1 - 2.2.3

## Hoe de pleister aanbrengen

Voor instructies, zie [ hoe te om een componentenflard toe te passen die door Adobe Commerce ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze steunkennisbasis wordt verstrekt.

## Nuttige koppelingen in onze gebruikershandleiding

* [ beheert Gearchiveerde orden ](https://docs.magento.com/user-guide/sales/order-archive.html)

## Bijgevoegde bestanden
