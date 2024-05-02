---
title: Product Recommendations niet weergegeven in Page Builder
description: Dit artikel biedt een oplossing voor het probleem waarbij de optie Product Recommendations niet wordt weergegeven in Page Builder.
exl-id: e96a446b-2e64-47a6-ac1b-e73183da9fb8
feature: Page Builder, Configuration, Personalization, Products, Recommendations
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
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
1. Als het het volgende bericht terugkeert: *Niet gevonden in pakket magento/module-page-builder-product-recommendations*, moet u het installeren door het bevel in werking te stellen: `composer require magento/module-page-builder-product-recommendations`

Als u Product Recommendations inschakelt in Page Builder, kunt u [een aanbeveling-eenheid toevoegen](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) op alle inhoud die is gemaakt in Page Builder.

## Gerelateerde lezing

* [Inhoud toevoegen - Product Recommendations](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) in onze gebruikershandleiding.
* [Product Recommendations installeren en configureren](https://devdocs.magento.com/recommendations/install-configure.html) in onze ontwikkelaarsdocumentatie.
* [Adobe Commerce-gebruikershandleiding](https://docs.magento.com/user-guide/)
