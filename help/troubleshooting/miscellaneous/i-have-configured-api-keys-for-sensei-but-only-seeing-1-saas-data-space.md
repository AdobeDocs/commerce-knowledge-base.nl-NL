---
title: Ik heb API sleutels voor Adobe AI gevormd maar slechts één SaaS gegevensruimte zien
description: Dit artikel biedt een oplossing voor de problemen waarbij slechts één SaaS-gegevensruimte wordt weergegeven nadat u de API-sleutels voor Adobe AI hebt geconfigureerd.
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 27b0836380c3040b26076b9cb81b9328cb2c9ff2
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Ik heb API sleutels voor Adobe AI gevormd maar slechts één SaaS gegevensruimte zien

Dit artikel biedt een oplossing voor de problemen waarbij slechts één SaaS-gegevensruimte wordt weergegeven nadat u de API-sleutels voor Adobe AI hebt geconfigureerd.

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden): alle versies
* Magento Open Source: alle versies
* Extensie of technologie (snel, New Relic, enz.), Adobe AI (productaanbevelingen/Live zoeken)

## Probleem

Ik heb de API sleutels voor Adobe AI gevormd, maar ik zie slechts één SaaS gegevensruimte.

## Oorzaak

Het aantal SaaS-gegevensruimten dat wordt weergegeven, is afhankelijk van uw Commerce-licentie:

* Adobe Commerce - Eén productiedeswitruimte; twee testgegevensruimten
* Magento Open Source - Eén gegevensruimte voor productie; geen gegevensruimten voor tests

## Oplossing

* Controleer of de API-sleutels zijn gemaakt op het account van de accounteigenaar. Zelfs als u gedeelde toegang tot hun account hebt gekregen en de sleutels voor uw eigen account hebt gemaakt, biedt dit u niet meer dan één gegevensruimte.
* Als de sleutels op de rekening van de Eigenaar van de Rekening werden geproduceerd, zorg ervoor dat de vergunning actief is, d.w.z., zijn er geen hangende facturen.
