---
title: Pas een patch toe om DHL als scheepvaartmaatschappij te blijven aanbieden
description: Dit artikel biedt een patch, waarmee handelaren die Adobe Commerce 2.4.4 en eerder gebruiken, DHL-scheepvaart kunnen blijven aanbieden nadat het DHL-schema 6.0 eind juli - september 2022 is vervangen.
exl-id: 4350e83a-495b-41b4-a526-dae5923e9d41
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Pas een patch toe om DHL als scheepvaartmaatschappij te blijven aanbieden


## Betrokken producten en versies

* Adobe Commerce 2.4.4 en eerder, alle plaatsingsmethodes.

## Probleem

DHL introduceert een 6.2 schema-versie en is eind juli - september 2022 afgekeurd. Adobe Commerce 2.4.4 en eerdere DHL-integratie ondersteunen alleen versie 6.0.

## Oplossing

Adobe Commerce 2.4.5, dat in augustus 2022 zal worden uitgebracht, zal de verbeterde integratie met DHL bevatten die het schema versie 6.2 gebruikt. Totdat de nieuwe versie wordt vrijgegeven (of in het geval u verkiest om niet te bevorderen), moedigen wij u aan om AC-3022 flard toe te passen, die versie 6.2 DHL schemasteun uitvoert, om DHL verzendingen in uw opslag na de afschrijving te blijven aanbieden.

## Reparatie

De patch-id is AC-3022 en is beschikbaar in versie 1.1.16 van het Hulpprogramma voor kwaliteitspatches.
Verwijs naar het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) > het artikel van het Gebruik ](https://devdocs.magento.com/quality-patches/usage.html) in onze ontwikkelaarsdocumentatie voor informatie over hoe te om QPT te gebruiken en flarden te installeren.

De patch is van toepassing op de volgende Adobe Commerce-versies:

* 2.4.0 - 2.4.4-p1
* 2.3.7.

## Gerelateerde lezing

* [ Verschepende Dragers > DHL ](https://docs.magento.com/user-guide/shipping/dhl.html) in onze gebruikersgids
* [ Methoden van de Levering ](https://docs.magento.com/user-guide/configuration/sales/delivery-methods.html) in onze gebruikersgids
