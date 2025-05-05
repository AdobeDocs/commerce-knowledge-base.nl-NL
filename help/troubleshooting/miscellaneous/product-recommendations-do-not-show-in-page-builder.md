---
title: Product Recommendations niet weergegeven in Page Builder
description: Dit artikel biedt een oplossing voor het probleem waarbij de optie Product Recommendations niet wordt weergegeven in Page Builder.
exl-id: e96a446b-2e64-47a6-ac1b-e73183da9fb8
feature: Page Builder, Configuration, Personalization, Products, Recommendations
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Product Recommendations niet weergegeven in Page Builder

Dit artikel biedt een oplossing voor het probleem waarbij de optie Product Recommendations niet wordt weergegeven in Page Builder.

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden)

## Probleem

De optie Recommendations van het product wordt niet weergegeven in Page Builder.

## Oorzaak

Er is geen optie in de Bouwer van de Pagina om Product Recommendations toe te voegen. Product Recommendations for Page Builder is een optionele module en wordt apart geïnstalleerd.

## Oplossing

1. Controleer of u de module afzonderlijk hebt geïnstalleerd door de opdracht uit te voeren: `composer show magento/module-page-builder-product-recommendations`
1. Als het het volgende bericht terugkeert: *Pakket magento/module-page-builder-product-aanbevelingen niet gevonden*, zult u het moeten installeren door het bevel in werking te stellen: `composer require magento/module-page-builder-product-recommendations`

Door Product Recommendations in de Bouwer van de Pagina toe te laten, zult u een aanbeveling eenheid [&#128279;](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html?lang=nl-NL) aan om het even welke inhoud kunnen toevoegen die in de Bouwer van de Pagina wordt gecreeerd.

## Gerelateerde lezing

* [ voeg Inhoud toe - product Recommendations ](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html?lang=nl-NL) in onze gebruikersgids.
* [ installeer en vorm Recommendations van het Product ](https://experienceleague.adobe.com/nl/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure) in onze ontwikkelaarsdocumentatie.
* [ de Gids van de Gebruiker van Adobe Commerce ](https://experienceleague.adobe.com/nl/docs/commerce-admin/user-guides/home)
