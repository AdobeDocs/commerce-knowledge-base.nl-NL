---
title: 504 gatewayonderbreking fout wanneer het opslaan van een categorie met 1k+ producten
description: Dit artikel stelt een oplossing voor de onderbrekingskwestie voor u zou kunnen hebben, wanneer het uitvoeren van verrichtingen met grote categorieën (1k+ plus producten).
exl-id: 1f4b0385-215d-4d3d-8704-986c090824aa
feature: Cache, Categories, Marketing Tools, Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Vereisten: De **Opslag** > **Configuratie** > **CATALOG** > **Catalogus** > **de Weg van de Categorieën van het Gebruik voor product URLs** optie wordt geplaatst aan *ja* voor uw opslagmening.

<u> Stappen om te reproduceren </u>

1. In Commerce Admin, ga naar **Catalogus** > **Categorieën**.
1. Open een grote categorie, zoals meer dan 1000 toegewezen producten.
1. Voeg een product toe aan de categorie.
1. Klik **sparen Categorie**.

<u> Verwacht resultaat:</u>

Categorie is opgeslagen.

<u> Ware resultaat:</u>

Na vijf minuten van opslagproces, verschijnt de pagina van de 504 gatewayonderbreking foutmelding.

## Oorzaak

Het proces duurt langer dan de geconfigureerde time-out van de server.

## Oplossing

Het onbruikbaar maken van **produceert &quot;categorie/product&quot;URL herschrijft** optie zal alle categorie/product URL herschrijft uit het gegevensbestand verwijderen, en beduidend de tijd verminderen die voor de verrichtingen met grote categorieën wordt vereist.

>[!WARNING]
>
>Als u deze optie uitschakelt, wordt de categorie/product-URL permanent verwijderd zonder dat de URL kan worden hersteld.

Om **onbruikbaar te maken produceer &quot;categorie/product&quot;URL herschrijft** optie:

1. In Commerce Admin, navigeer aan **Opslag** > **Configuratie** > **CATALOG** > **Catalogus**.
1. In de hoogste linkerhoek van de configuratiepagina, op het **gebied van het Toepassingsgebied**, plaats uw configuratiewerkingsgebied aan *Standaard Config*.
1. De reeks **produceert &quot;categorie/product&quot;URL herschrijft** aan *Nr*.
1. Klik **sparen Config**.
1. Cache opschonen door uit te voeren    ```bash    bin/magento cache:clean    ```    of in Commerce Admin onder **Systeem** > **Hulpmiddelen** > **Beheer van het Geheime voorgeheugen**.

Nu kunt u doorgaan met het toevoegen van producten aan categorieën of het verplaatsen van categorieën met een groot aantal producten. Deze bewerkingen nemen veel minder tijd in beslag en leiden niet tot time-out.

## Gerelateerde lezing

[&#x200B; Automatische Omleiding van het Product &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/marketing/seo/url-rewrites/url-redirect-product-automatic) in onze gebruikersgids.
