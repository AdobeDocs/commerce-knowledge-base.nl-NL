---
title: Fout ''Reeds ingesteld gebied'' bij opslaan van themeconfiguratie in Admin
description: Dit artikel bevat een patch voor het bekende Adobe Commerce-probleem met cloudinfrastructuur 2.2.4 dat betrekking heeft op het ophalen van het foutbericht *"Gebied is al ingesteld"* wanneer wordt geprobeerd een thema in te stellen voor de standaardwinkelweergave in Commerce Admin.
exl-id: c4e34a73-b774-4447-ba8e-aaf208ad54c5
feature: Admin Workspace, Configuration, Themes
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Fout bij het opslaan van de themaconfiguratie in Admin

Dit artikel verstrekt een flard voor bekende Adobe Commerce op de kwestie van de wolkeninfrastructuur 2.2.4 met betrekking tot het krijgen van *&quot;Gebied is reeds plaatste&quot;* foutenmelding wanneer het proberen om een thema voor de Mening van de StandaardOpslag in Commerce Admin te plaatsen.

## Probleem

U krijgt &quot; *iets ging verkeerd terwijl het opslaan van deze configuratie: Het gebied is reeds plaatste* &quot; foutenmelding wanneer het proberen om een thema voor de Mening van de StandaardOpslag te plaatsen.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij de Commerce-beheerder.
1. Navigeer aan **Inhoud** > **Ontwerp** > **Configuratie**.
1. Plaats het configuratiewerkingsgebied aan *StandaardMening van de Opslag*.
1. Verander het thema in de **Toegepaste drop-down van het Thema**. Bijvoorbeeld, van *Luma* aan *Lege.*
1. Klik **sparen Configuratie**.

<u> Verwacht resultaat </u>: Het geselecteerde thema wordt toegepast voor de standaardarchiefmening.

<u> Werkelijk resultaat </u> : Het thema wordt niet toegepast, *&quot;Het iets ging verkeerd terwijl het opslaan van deze configuratie: Het gebied is reeds plaatste&quot;* foutenmelding wordt getoond.

## Reparatie

De patch is aan dit artikel gekoppeld. Klik op de volgende koppeling of schuif omlaag naar het einde van het artikel en klik op het bijgevoegde bestand om het te downloaden:

[Download MDVA-11106\_EE\_2.2.4\_v1.composer.patch](assets/MDVA-11106_EE_2.2.4_v1.composer.patch.zip)

## Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce over wolkeninfrastructuur 2.2.4

De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce op cloudinfrastructuur 2.0.X
* Adobe Commerce op cloudinfrastructuur 2.1.X
* Adobe Commerce over cloudinfrastructuur 2.2.0 - 2.2.5
* Adobe Commerce op locatie 2.0.X
* Adobe Commerce op locatie 2.1.X
* Adobe Commerce op locatie 2.2.0 - 2.2.5

## Hoe de pleister aanbrengen

Voor instructies, zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze steunkennisbasis wordt verstrekt.

## Bijgevoegde bestanden
