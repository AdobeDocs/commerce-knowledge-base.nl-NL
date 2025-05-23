---
title: Problemen na het uitschakelen van een module
description: Dit artikel biedt een oplossing voor problemen met de modulefunctionaliteit nadat de uitvoer van de module in Commerce Admin is uitgeschakeld.
exl-id: 517f6993-f09e-4a94-8c57-175ecf9a98a8
feature: Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---

# Problemen na het uitschakelen van een module

Dit artikel biedt een oplossing voor problemen met de modulefunctionaliteit nadat de uitvoer van de module in Commerce Admin is uitgeschakeld.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur 2.1.X of lager
* Adobe Commerce op locatie 2.1.X of eerder

## Probleem

Het hebben van gehandicapte moduleoutput in Commerce Admin, onder **Slaat** > **Montages** > **Configuratie** > GEAVANCEERD > **Geavanceerd**, zou u kwesties met betrekking tot de modulefunctionaliteit kunnen beginnen te zien.

## Oorzaak

Het onbruikbaar maken van een moduleoutput onder **Slaat** > **Montages** > **Configuratie** > GEAVANCEERD > **Geavanceerd** maakt slechts de output (HTML, JS) onbruikbaar, maar het maakt niet de functionaliteit van deze module onbruikbaar.

## Oplossing

Als u modulefunctionaliteit moet onbruikbaar maken, maak de module zoals die in [ wordt beschreven toe of onbruikbaar maakt modules ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/tutorials/manage-modules) in onze ontwikkelaarsdocumentatie.

De functie voor het uitschakelen van de module-uitvoer is verwijderd vanaf versie 2.2.0.
