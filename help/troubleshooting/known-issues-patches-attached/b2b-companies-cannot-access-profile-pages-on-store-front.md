---
title: '''B2B: Bedrijven hebben geen toegang tot profielpagina''s op winkelvoorzijde'''
description: Dit artikel bevat een patch voor het bekende Adobe Commerce 2.2.4 B2B-probleem dat betrekking heeft op geregistreerde bedrijven die fouten ophalen op hun accountpagina's in de winkel.
exl-id: 5f0d81a2-e0a1-487b-8a4f-28b8cb704e32
feature: B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# B2B: Bedrijven hebben geen toegang tot profielpagina&#39;s op winkelvoorzijde

Dit artikel bevat een patch voor het bekende Adobe Commerce 2.2.4 B2B-probleem dat betrekking heeft op geregistreerde bedrijven die fouten ophalen op hun accountpagina&#39;s in de winkel.

## Probleem

De klanten (bedrijven) kunnen tot een bedrijfrekening op de plaats succesvol leiden, maar krijgen *&quot;Geen dergelijke entiteit met customerId = &quot;* en *&quot;U hebt nog geen bedrijfrekening&quot;* foutenmeldingen. Zij kunnen *&quot;500 Interne Fout van de Server&quot;* ook krijgen wanneer het proberen om tot de pagina van het Profiel van het Bedrijf toegang te hebben.

## Reparatie

Als u het archief met een patch wilt downloaden, klikt u op de volgende koppeling:

[MDVA-9013\_EE\_2.2\_composer.patch downloaden](assets/MDVA-9013_EE_2.2.2_composer.patch.zip)

### Compatibele Adobe Commerce-versies

De patch is gemaakt voor:

* Adobe Commerce op locatie 2.2.2

De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce op cloudinfrastructuur van 2.2.0 tot 2.2.4
* Adobe Commerce op locatie van 2.2.0 tot en met 2.2.1 en van 2.2.3 tot en met 2.2.4

## Hoe de pleister aanbrengen

Zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies wordt verstrekt.
