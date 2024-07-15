---
title: Adobe Commerce op cloudinfrastructuur v2.3.5 Invalidatie van GraphQL-caching werkt niet
description: Dit artikel verstrekt een flard voor de kwestie waar het verzoek van GraphQL ` GET ` achterhaalde informatie terugkeert als de klant productinformatie verandert.
exl-id: 10ae52bd-e71a-42e3-9600-7a9713903815
feature: GraphQL, Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Adobe Commerce op cloudinfrastructuur v2.3.5 Invalidatie van GraphQL-caching werkt niet

Dit artikel bevat een patch voor het probleem waarbij met een GraphQL `GET` -aanvraag verouderde informatie wordt geretourneerd als de klant productinformatie wijzigt.

## Betrokken producten en versies

Adobe Commerce on cloud Infrastructure v2.3.5.

## Probleem

GraphQL-verzoeken worden snel in het cachegeheugen opgeslagen en de versie in het cachegeheugen wordt opgehaald voor elk volgend verzoek van Fastly. Als een product opnieuw wordt opgeslagen in de Adobe Commerce-backend, maakt de Fastly-cache de validatie ongedaan wanneer een product wordt bijgewerkt. Het blijft echter geldig.

<u> Stappen om </u> te reproduceren:

1. Activeer het volgende GraphQL-verzoek om producten voor bijvoorbeeld bepaalde rubrieken op te halen:
   <pre><magento2-server>
    </pre>
1. Sla een van de producten die in de bovenstaande aanvraag zijn opgehaald, opnieuw op in Commerce Admin.
1. Trigger het verzoek opnieuw.

<u> Verwachte resultaten </u>:

De header `X-Cache` bevat `MISS` .

<u> Ware resultaten </u>:

De header `X-Cache` bevat `HIT` , wat betekent dat de reactie in de cache wordt geplaatst.

## Oplossing

Schakel de GraphQL-productcache uit met de patch die in dit artikel is opgegeven.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[MDVA-28559\_EE\_2.3.5-p1\_COMPOSER\_v1.patch](assets/MDVA-28559_EE_2.3.5-p1_v1.composer.patch.zip)

### Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce op cloudinfrastructuur v2.3.5

De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce op cloudinfrastructuur v2.4.0
* Adobe Commerce op locatie v2.4.0
* Adobe Commerce on cloud Infrastructure v2.3.5-p2
* Adobe Commerce op locatie v2.3.5-p2
* Adobe Commerce op cloudinfrastructuur v2.3.5-p1
* Adobe Commerce op locatie v2.3.5-p1
* Adobe Commerce op locatie v2.3.5
* Adobe Commerce on cloud Infrastructure v2.3.4-p2
* Adobe Commerce op locatie v2.3.4-p2
* Adobe Commerce op cloudinfrastructuur v2.3.4
* Adobe Commerce op locatie v2.3.4
* Adobe Commerce op locatie v2.3.3-p1
* Adobe Commerce op locatie v2.3.3

## Hoe de pleister aanbrengen

Zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies op wordt verstrekt hoe te om een composerflard toe te passen.

## Bijgevoegde bestanden
