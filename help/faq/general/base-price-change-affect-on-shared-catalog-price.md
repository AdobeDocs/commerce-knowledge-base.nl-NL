---
title: Basisprijswijziging is van invloed op de prijs van een gedeelde catalogus
description: 'In dit artikel wordt de vraag beantwoord: als een product in een gedeelde catalogus een aangepaste prijs heeft en de basisprijs van het product wijzigt (bijvoorbeeld na een geplande update), welke prijs geldt dan in de gedeelde catalogus?'
exl-id: 916678c1-ada6-4f23-af16-b107cb83ff16
feature: Catalog Management
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# Basisprijswijziging is van invloed op de prijs van een gedeelde catalogus

In dit artikel wordt de vraag beantwoord: als een product in een gedeelde catalogus een aangepaste prijs heeft en de basisprijs van het product wijzigt (bijvoorbeeld na een geplande update), welke prijs geldt dan in de gedeelde catalogus?

## Als de aangepaste prijs is ingesteld op Percentage, verandert de prijs van de gedeelde catalogus ook

Als de aangepaste prijs voor een product in een gedeelde catalogus is ingesteld op Percentage, wordt de prijs van de gedeelde catalogus van het product impliciet bijgewerkt nadat de basisprijs is gewijzigd.

Met andere woorden, wanneer de basisprijs wordt bijgewerkt (via een normale of geplande update), verandert de prijs van de gedeelde catalogus ook na het toepassen van de percentagekorting.

## Als de aangepaste prijs is ingesteld op Vast, verandert de prijs van de gedeelde catalogus niet

Als de aangepaste prijs voor een product in een gedeelde catalogus is ingesteld op Vast, verandert de prijs in de gedeelde catalogus nooit - ongeacht de manier waarop de basisprijs wordt bijgewerkt (via geplande update, Adobe Commerce Admin, API of importeren).

## Met Storefront wordt altijd de laagste beschikbare prijs weergegeven

Als de basisprijs van het product verandert en minder dan de overeenkomstige gedeelde catalogusprijs wordt, toont de Storefront de basisprijs als laagste beschikbare prijs in het systeem.

## Gerelateerde lezing

[ Vastgestelde Prijsbepaling en Structuur voor een Gedeelde Catalogus ](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/define/catalog-shared-pricing-structure.html?lang=nl-NL) in onze gebruikersgids.
