---
title: Ik heb API sleutels voor Sensei gevormd maar slechts één SaaS gegevensruimte zien
description: Dit artikel biedt een oplossing voor de problemen waarbij slechts één SaaS-gegevensruimte wordt weergegeven nadat u de API-sleutels voor Sensei hebt geconfigureerd.
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Ik heb API sleutels voor Sensei gevormd maar slechts één SaaS gegevensruimte zien

Dit artikel biedt een oplossing voor de problemen waarbij slechts één SaaS-gegevensruimte wordt weergegeven nadat u de API-sleutels voor Sensei hebt geconfigureerd.

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden): alle versies
* Magento Open Source: alle versies
* Extensie of technologie (Fastly, New Relic, enz.), Adobe Sensei (Product Recommendations/Live Search)

## Probleem

Ik heb de API sleutels voor Sensei gevormd, maar ik zie slechts één SaaS gegevensruimte.

## Oorzaak

Het aantal SaaS-gegevensruimten dat wordt weergegeven, is afhankelijk van uw Commerce-licentie:

* Adobe Commerce - Eén productiedeswitruimte; twee testgegevensruimten
* Magento Open Source - Eén gegevensruimte voor productie; geen gegevensruimten voor tests

## Oplossing

* Controleer of de API-sleutels zijn gemaakt op het account van de accounteigenaar. Zelfs als u gedeelde toegang tot hun account hebt gekregen en de sleutels voor uw eigen account hebt gemaakt, biedt dit u niet meer dan één gegevensruimte.
* Als de sleutels op de rekening van de Eigenaar van de Rekening werden geproduceerd, zorg ervoor dat de vergunning actief is, d.w.z., zijn er geen hangende facturen.
