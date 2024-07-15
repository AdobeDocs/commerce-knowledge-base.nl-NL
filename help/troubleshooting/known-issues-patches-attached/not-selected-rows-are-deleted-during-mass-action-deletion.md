---
title: Meer producten zijn verwijderd dan was gestart tijdens massaal verwijderen in Admin
description: Dit artikel biedt een patch voor de bekende Adobe С handel in cloudinfrastructuur 2.2.3-kwestie met betrekking tot het niet verwijderen van geselecteerde records wanneer een bulkverwijdering wordt uitgevoerd in een raster in Commerce Admin.
exl-id: 0bfdc84e-0292-4702-a20e-bdbe67c111a2
feature: Admin Workspace, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Meer producten zijn verwijderd dan was gestart tijdens massaal verwijderen in Admin

Dit artikel biedt een patch voor de bekende Adobe С handel in cloudinfrastructuur 2.2.3-kwestie met betrekking tot het niet verwijderen van geselecteerde records wanneer een bulkverwijdering wordt uitgevoerd in een raster in Commerce Admin.

## Probleem

In Admin, als u klant of cliëntverslagen selecteert om worden geschrapt, filter het net, en selecteer dan de **Schrapping** actie, worden alle verslagen geschrapt.

<u> Stappen om </u> te reproduceren:

1. Navigeer aan **Catalogus** > **Producten** in Admin.
1. Selecteer een product of meerdere producten.
1. Selecteer Verwijderen in het vervolgkeuzemenu Handelingen.

<u> Verwachte resultaten </u>:

Alleen geselecteerde producten worden verwijderd.

<u> Ware resultaten </u>:

Sommige andere producten worden ook verwijderd.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[Download MDVA-10600\_EE\_2.2.3\_v1.composer.patch](assets/MDVA-10600_EE_2.2.3_v1.composer.patch.zip)

### Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce over wolkeninfrastructuur 2.2.3

De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce op locatie 2.1.8-2.1.14, 2.2.0-2.2.2 en 2.2.4-2.2.5
* Adobe Commerce op cloudinfrastructuur 2.2.4-2.2.5

## Hoe de pleister aanbrengen

Zie [ hoe te om een componentenflard toe te passen die door Adobe Commerce ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies wordt verstrekt.
