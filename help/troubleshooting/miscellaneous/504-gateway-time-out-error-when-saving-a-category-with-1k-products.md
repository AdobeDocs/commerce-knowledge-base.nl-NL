---
title: 504 gatewayonderbreking fout wanneer het opslaan van een categorie met 1k+ producten
description: Dit artikel stelt een oplossing voor de onderbrekingskwestie voor u zou kunnen hebben, wanneer het uitvoeren van verrichtingen met grote categorieën (1k+ plus producten).
exl-id: 1f4b0385-215d-4d3d-8704-986c090824aa
feature: Cache, Categories, Marketing Tools, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# 504 gatewayonderbreking fout wanneer het opslaan van een categorie met 1k+ producten

Dit artikel stelt een oplossing voor de onderbrekingskwestie voor u zou kunnen hebben, wanneer het uitvoeren van verrichtingen met grote categorieën (1k+ plus producten).

## Betrokken producten en versies:

* Adobe Commerce over wolkeninfrastructuur 2.3.3
* Adobe Commerce op locatie 2.3.3
* Magento Open Source 2.3.3

## Probleem

Vereisten: de **Winkels** > **Configuratie** > **CATALOGUS** > **Catalogus** > **Categoriepad gebruiken voor product-URL&#39;s** optie is ingesteld op *Ja* voor de winkelweergave.

<u>Stappen om te reproduceren</u>

1. Ga in Commerce Admin naar **Catalogus** > **Categorieën**.
1. Open een grote categorie, zoals meer dan 1000 toegewezen producten.
1. Voeg een product toe aan de categorie.
1. Klikken **Categorie opslaan**.

<u>Verwacht resultaat:</u>

Categorie is opgeslagen.

<u>Werkelijk resultaat:</u>

Na vijf minuten van opslagproces, verschijnt de pagina van de 504 gatewayonderbreking foutmelding.

## Oorzaak

Het proces duurt langer dan de geconfigureerde time-out van de server.

## Oplossing

Het onbruikbaar maken van **URL voor &quot;categorie/product&quot; genereren Herschrijvingen** Als u deze optie kiest, worden alle herschrijvingen van de categorie-/product-URL uit de database verwijderd en wordt de tijd die nodig is voor bewerkingen met grote categorieën aanzienlijk korter.

>[!WARNING]
>
>Als u deze optie uitschakelt, wordt de categorie/product-URL permanent verwijderd zonder dat de URL kan worden hersteld.

Om het **URL voor &quot;categorie/product&quot; genereren Herschrijvingen** optie:

1. Navigeer in Commerce Admin naar **Winkels** > **Configuratie** > **CATALOGUS** > **Catalogus**.
1. In de linkerbovenhoek van de configuratiepagina, in **Toepassingsgebied** gebied, plaats uw configuratiewerkingsgebied aan *Standaardconfiguratie*.
1. Set **URL voor &quot;categorie/product&quot; genereren Herschrijvingen** tot *Nee*.
1. Klikken **Config opslaan**.
1. Cache opschonen door uit te voeren    ```bash    bin/magento cache:clean    ```    of in Commerce Admin onder **Systeem** > **Gereedschappen** > **Cachebeheer**.

Nu kunt u doorgaan met het toevoegen van producten aan categorieën of het verplaatsen van categorieën met een groot aantal producten. Deze bewerkingen nemen veel minder tijd in beslag en leiden niet tot time-out.

## Gerelateerde lezing

[Automatische productomleiding](https://docs.magento.com/user-guide/v2.3/marketing/url-redirect-product-automatic.html) in onze gebruikershandleiding.
