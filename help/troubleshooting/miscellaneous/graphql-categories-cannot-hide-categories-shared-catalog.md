---
title: GraphQL-query voor het verbergen van categorieën die niet werken met een gedeelde B2B-catalogus
description: Dit artikel biedt een oplossing wanneer de functie voor gedeelde B2B-catalogus niet werkt met een query voor GraphQL-categorieën om categorieën te verbergen.
exl-id: bdafa8d9-b637-409e-86b5-d132bccfe0b8
feature: B2B, Catalog Management, Categories, GraphQL, Customer Service
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# GraphQL-query voor het verbergen van categorieën die niet werken met een gedeelde B2B-catalogus


## Betrokken producten en versies

* Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.4.3

## Probleem

GraphQL-categorieën en `categoryList` -query&#39;s negeren de categorietoestemming om categorieën in een gedeelde catalogus te verbergen. Dit gebeurt bij alle verkopers op Adobe Commerce 2.4.3 met B2B Gedeelde functie van de Catalogus ingeschakeld.

<u> Stappen om </u> te reproduceren:

Vereisten:

Dit gebeurt bij alle verkopers op Adobe Commerce 2.4.3 met PWA storefront die GraphQL API met Adobe Commerce backend/Admin verbruiken die B2B Gedeelde eigenschap van de Catalogus aanzetten.

1. Meerdere categorieën maken (CAT1,CAT2).
1. Een persoonlijke gedeelde catalogus maken.
1. Maak een zakelijke gebruiker en wijs deze toe aan de bovenstaande gedeelde catalogus.
1. Wijs een paar producten aan elk van deze categorieën toe.
1. Wijs CAT1 aan de douanecatalogus toe, unassign CAT2 van de douane privé catalogus. Hierdoor worden alle producten van CAT2 uit de gedeelde catalogus verwijderd.
1. Sla de aangepaste catalogus op.
1. Plaats de categorietoestemming voor CAT2 aan *ontken* het doorbladeren categorie en de klantengroep plaatsen aan de bovengenoemde privé catalogus.
1. Voer de query `categoryList query` of de categoriesquery uit als de bedrijfsgebruiker van stap drie.

<u> Verwachte resultaten </u>:

Alleen de CAT1 wordt weergegeven in de resultaten.

<u> Ware resultaten </u>:

Alle categorieën worden weergegeven, ongeacht of ze zijn toegewezen/niet toegewezen in de gedeelde catalogus of wat de categorietoestemmingen zijn.

## Oorzaak

Functionaliteit is niet geïmplementeerd.

## Oplossing

De kwestie zal in het werkingsgebied van versie 2.4.4 worden bevestigd, en de handelaren zouden [ een kaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) moeten voorleggen om een douaneflard te krijgen als zij een oplossing voorafgaand aan 2.4.4 versie nodig hebben.

## Gerelateerde lezing

* [ aantal van de beste praktijken Adobe Commerce van categoriegrenzen ](https://support.magento.com/hc/en-us/articles/360048176832) in onze basis van de steunkennis.
