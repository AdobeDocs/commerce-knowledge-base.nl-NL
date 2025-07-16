---
title: Verhoogde uitvoeringstijd voor bulkasynchrone webeindpunten na APSB25-08-beveiligingspatch
description: Dit artikel biedt een hotfix voor het probleem waarbij POST-rusten/all/async/bulk/V1/products-aanvragen voor 1000+-items na het toepassen van de APSB25-08-beveiligingspatch aanzienlijk meer uitvoeringstijd hebben.
feature: Security, Cache, REST, Products, Customers
role: Admin, Developer
exl-id: 784a48cb-1ef1-432b-b09f-ebcbb9bebf01
source-git-commit: f0c2e20e0bd6dab713be59c1c686ee2948445bd4
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Verhoogde uitvoeringstijd voor alle bulkasynchrone webeindpunten na APSB25-08-beveiligingspatch

Dit artikel biedt een hotfix voor alle asynchrone webeindpunten in bulk, zoals `POST rest/all/async/bulk/V1/products` , met 1000+ items die aanzienlijk langere uitvoeringstijden ondervinden na het toepassen van de beveiligingspatch voor APSB25-08.

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden) 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4-p9 10, 2.4.4-p11, 2.4.4-p12

* Adobe Commerce (alle implementatiemethoden) 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p9 10, 2.4.5-p11

* Adobe Commerce (alle implementatiemethoden) 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8, 2.4.6-p9

* Adobe Commerce (alle implementatiemethoden) 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3, 2.4.7-p4

* Adobe Commerce (alle implementatiemethoden) 2.4.8

## Probleem

Nadat u de beveiligingspatch voor APSB25-08 hebt toegepast, duurt het aanzienlijk langer om `POST rest/all/async/bulk/V1/products` -aanvragen met 1000+-items uit te voeren.

<u> Stappen om </u> te reproduceren:

1. Voer een `POST rest/all/async/bulk/V1/products` -aanvraag in met meer dan 1000 items (naam, SKU en beschrijving zijn voldoende).
1. Noteer de tijd die u voor het verzoek hebt uitgetrokken.
1. Pas het beveiligingspatch APSB25-08 toe en maak gegenereerde gegevens en cache schoon met `se:di:co` .
1. Voer `bin/magento c:f` uit.
1. Ga naar de winkel om ervoor te zorgen dat de cache en gegenereerde bestanden aanwezig zijn.
1. Herhaal de aanvraag uit stap 1.
1. Let op de extra tijd die u voor het verzoek hebt uitgetrokken.
1. Verwijder het beveiligingspatch APSB25-08, verwijder het cachegeheugen, regenerate de code en herhaal het verzoek uit stap 1 om te bevestigen dat de uitvoeringstijd weer normaal wordt. (Optioneel)

<u> Verwachte resultaten </u>:

De uitvoeringstijd voor `async/bulk` -aanvragen is aanzienlijk verlengd nadat de beveiligingspatch is toegepast.

<u> Ware resultaten </u>:

De uitvoeringstijd voor `async/bulk` -aanvragen had na het toepassen van de beveiligingspatch niet significant mogen zijn verlengd, hoewel enige tijdigheid wordt verwacht.

## Oplossing

Om de kwestie op te lossen, pas [ AC-14078-2-4x-composer-patch.zip ](assets/AC-14078-2-4x-composer-patch.zip) toe.

## Hoe de pleister aanbrengen

Pak het dossier uit en zie [ hoe te om een componentenflard toe te passen die door Adobe ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) in onze basis van steunkennis voor instructies wordt verstrekt.

## Gerelateerde lezing

* [ de update van de Veiligheid beschikbaar voor Adobe Commerce - APSB25-08 ](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27149)
