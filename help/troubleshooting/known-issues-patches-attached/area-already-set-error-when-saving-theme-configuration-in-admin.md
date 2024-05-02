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

Dit artikel bevat een patch voor het bekende Adobe Commerce-probleem met cloudinfrastructuur 2.2.4 dat betrekking heeft op het ophalen van de *&quot;Gebied is al ingesteld&quot;* foutbericht bij het instellen van een thema voor de standaardwinkelweergave in Commerce Admin.

## Probleem

Je krijgt de &quot; *Er is iets misgegaan tijdens het opslaan van deze configuratie: Gebied is al ingesteld* &#39;&#39; foutbericht tijdens het instellen van een thema voor de standaardwinkelweergave.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de Commerce-beheerder.
1. Navigeren naar **Inhoud** > **Ontwerp** > **Configuratie**.
1. Stel het configuratiebereik in op *Standaardwinkelweergave*.
1. Het thema wijzigen in het dialoogvenster **Toegepast thema** vervolgkeuzelijst. Bijvoorbeeld van *Luminantie* tot *Leeg.*
1. Klikken **Configuratie opslaan**.

<u>Verwacht resultaat</u>: Het geselecteerde thema wordt toegepast voor de standaardwinkelweergave.

<u>Werkelijk resultaat</u> : Het thema wordt niet toegepast, de *&quot;Er is iets fout gegaan tijdens het opslaan van deze configuratie: het gebied is al ingesteld&quot;* foutbericht wordt weergegeven.

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

Zie voor instructies [Hoe een door Adobe geleverde componentpleister aanbrengen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze kennisbasis voor ondersteuning.

## Bijgevoegde bestanden
