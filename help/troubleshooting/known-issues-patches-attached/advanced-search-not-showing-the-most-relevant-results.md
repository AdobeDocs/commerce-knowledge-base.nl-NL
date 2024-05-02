---
title: Geavanceerd zoeken geeft niet de meest relevante resultaten weer
description: Dit artikel bevat een patch voor het bekende Adobe Commerce-probleem, waarbij de meest relevante resultaten niet eerst worden weergegeven in de geavanceerde zoekopdracht.
exl-id: 88f0782d-ba7d-4f19-9761-7894d978d334
feature: Search
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Geavanceerd zoeken geeft niet de meest relevante resultaten weer

Dit artikel bevat een patch voor het bekende Adobe Commerce-probleem, waarbij de meest relevante resultaten niet eerst worden weergegeven in de geavanceerde zoekopdracht.

## Betrokken versies {#Advancedsearchnotshowingmostrelevantresults-Affectedversions}

* Adobe Commerce (alle implementatieopties) 2.x.x
* Magento Open Source 2.x.x

## Probleem {#Advancedsearchnotshowingmostrelevantresults-Description}

De geavanceerde zoekfunctie retourneert niet eerst de meest relevante resultaten, zoals de snelle zoekopdracht doet. Het probleem is niet afhankelijk van het geselecteerde type zoekmachine.

<u>Stappen om te reproduceren:</u>

1. Ga in de winkel naar de snelzoekfunctie en zoek naar &quot;Flitsomslag&quot;.
1. Opmerking &quot;Orion Two-Tone Fitting Jacket&quot; is het eerste resultaat.
1. Ga naar Geavanceerde zoekopdracht en zoek naar &#39;&#39;Geschikt jasje&#39;&#39; in het naamveld.

<u>Verwacht resultaat:</u>

Het &quot;Orion Two-Tone Gedichte Jasje&quot;is het eerste resultaat wanneer het gebruiken van Geavanceerd onderzoek, als het meest relevante resultaat.

<u>Werkelijk resultaat:</u>

Het &quot;Orion Two-Tone Fitting Jacket&quot; is niet het eerste resultaat, hoewel het het meest relevant is.

## Oplossing {#Advancedsearchnotshowingmostrelevantresults-Solution}

U kunt dit probleem oplossen door de patch toe te passen die aan dit artikel is gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[Download MDVA-7256\_EE\_2.1.7\_v1.composer.patch](assets/MDVA-7256_EE_2.1.7_v1.composer.patch.zip)

De patch voegt de implementatie voor sorteren toe op relevantie voor geavanceerde zoekresultaten als het standaardsorteerveld.

De patch is compatibel met alle betrokken versies en versies.

## Hoe de pleister aanbrengen

Zie voor instructies [Hoe een door Adobe geleverde componentpleister aanbrengen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze kennisbasis voor ondersteuning.

## Bijgevoegde bestanden
