---
title: Verzending neerhalen onjuist adres
description: De verzendoplossing haalt het adres van de bron van het product niet op.
exl-id: ce89713f-d506-4e4f-bf49-cdee3e6d29b5
feature: Customer Service, Orders, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# Verzending neerhalen onjuist adres

## Probleem

De verzendoplossing haalt het adres van de bron van het product niet op.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur (alle versies), met Magento Inventory geïnstalleerd
* Adobe Commerce op locatie 2.3.0 en hoger, met Magento Inventory geïnstalleerd
* Magento Open Source 2.3.0 en hoger, met Magento Inventory geïnstalleerd

### Oorzaak

Magento Inventory biedt momenteel geen ondersteuning voor het berekenen van verzendkosten op basis van het bronadres tijdens het afrekenen. In plaats daarvan wordt het standaardopslagadres van config gebruikt in alle gevallen.

## Verwante lezing

* [Veelgestelde vragen over Magento-inventarisatie](https://github.com/magento/inventory/wiki/MSI-FAQs) in GitHub.
