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

GraphQL-categorieën en `categoryList` wordt de categorietoestemming genegeerd om categorieën in een gedeelde catalogus te verbergen. Dit gebeurt bij alle verkopers op Adobe Commerce 2.4.3 met B2B Gedeelde functie van de Catalogus ingeschakeld.

<u>Stappen om te reproduceren</u>:

Vereisten:

Dit gebeurt bij alle verkopers op Adobe Commerce 2.4.3 met PWA storefront die GraphQL API met Adobe Commerce backend/Admin verbruiken die B2B Gedeelde eigenschap van de Catalogus aanzetten.

1. Meerdere categorieën maken (CAT1,CAT2).
1. Een persoonlijke gedeelde catalogus maken.
1. Maak een zakelijke gebruiker en wijs deze toe aan de bovenstaande gedeelde catalogus.
1. Wijs een paar producten aan elk van deze categorieën toe.
1. Wijs CAT1 aan de douanecatalogus toe, unassign CAT2 van de douane privé catalogus. Hierdoor worden alle producten van CAT2 uit de gedeelde catalogus verwijderd.
1. Sla de aangepaste catalogus op.
1. Stel de categorietoestemming voor CAT2 in op *Weigeren* In de categorie bladeren en de klantengroep instellen op de bovenstaande persoonlijke catalogus.
1. Voer de `categoryList query` of de categorieën vragen als bedrijfgebruiker van stap drie.

<u>Verwachte resultaten</u>:

Alleen de CAT1 wordt weergegeven in de resultaten.

<u>Werkelijke resultaten</u>:

Alle categorieën worden weergegeven, ongeacht of ze zijn toegewezen/niet toegewezen in de gedeelde catalogus of wat de categorietoestemmingen zijn.

## Oorzaak

Functionaliteit is niet geïmplementeerd.

## Oplossing

De kwestie zal in het toepassingsgebied van versie 2.4.4 worden geregeld en handelaren zouden [een ticket verzenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om een aangepaste pleister aan te brengen als zij een oplossing nodig hebben vóór de release van 2.4.4.

## Gerelateerde lezing

* [Beste praktijken Adobe Commerce aantal rubrieken limieten](https://support.magento.com/hc/en-us/articles/360048176832) in onze kennisbasis voor ondersteuning.
