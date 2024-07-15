---
title: Stock status is onjuist na Inventory management-installatie
description: Dit artikel bevat een oplossing voor het onjuist zijn van de voorraadstatus na installatie/upgrade van Inventory management.
exl-id: ae32fbe3-deab-4f31-b427-95f8b54a476f
feature: Install, Inventory, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Stock status is onjuist na Inventory management-installatie

Dit artikel bevat een oplossing voor het onjuist zijn van de voorraadstatus na installatie/upgrade van Inventory management.

## Voorraadstatus onjuist op sommige locaties

Na de eerste installatie of upgrade om Inventory management in de Adobe Commerce-omgeving met meerdere websites te hebben, hebben niet alle websites de juiste voorraadstatus voor producten.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, alle versies, met Inventory management geïnstalleerd
* Adobe Commerce op locatie 2.3.0 en hoger, met Inventory management geïnstalleerd
* Magento Open Source 2.3.0 en hoger, met Inventory management geïnstalleerd

## Oorzaak

Wanneer u installeert/bevordert, worden al uw producten toegewezen aan de standaardbron, associerend alle hoeveelheden aan die bron. De standaard-Source wordt toegewezen aan de standaardvoorraad, waarbij de standaardwebsite is gekoppeld.

## Oplossing

Als u meerdere websites hebt, moet u deze websites als Sales Channel toevoegen aan de standaardvoorraad of andere aangepaste bestanden.

Zie de [ sectie van de Beeld van de wiki/gebruikershandleiding ](https://docs.magento.com/m2/ce/user_guide/catalog/inventory-stock.html) in onze gebruikersgids voor details op hoe te om dit te doen.
