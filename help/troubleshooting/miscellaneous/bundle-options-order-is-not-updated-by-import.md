---
title: Volgorde van bundelopties wordt niet bijgewerkt door importeren
description: Dit artikel biedt een oplossing voor het probleem wanneer de opties voor het bundelproduct na het importeren van producten uit een CSV-bestand in een andere volgorde worden weergegeven dan in het importbestand.
exl-id: 7f7bf782-4b35-4067-aa94-417097079f1f
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# Volgorde van bundelopties wordt niet bijgewerkt door importeren

Dit artikel biedt een oplossing voor het probleem wanneer de opties voor het bundelproduct na het importeren van producten uit een CSV-bestand in een andere volgorde worden weergegeven dan in het importbestand.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur 2.2.x, 2.3.x
* Adobe Commerce op locatie 2.2.x, 2.3.x
* Magento Open Source

## Probleem

<u> Eerste vereisten </u>:

U hebt een geldig CSV-bestand met bundelproducten.

<u> Stappen om </u> te reproduceren:

1. Importeer het dossier gebruikend de [ functionaliteit van de Invoer ](https://docs.magento.com/m2/ee/user_guide/system/data-import.html).
1. Open de productpagina van de bundel.

<u> Verwachte resultaten </u>:

De volgorde van opties is gelijk aan die in het CSV-bestand.

<u> Ware resultaten </u>:

De volgorde van opties verschilt van die in het CSV-bestand.

## Oorzaak

De positie van de opties is niet expliciet gedeclareerd.

## Oplossing

1. Declareer expliciet een positie voor elke optie in de parameter `position` van de kolom `bundle_values` in het .csv-bestand. Voor gedetailleerde instructies, zie [ de Gegevens van het Product ](https://docs.magento.com/m2/ee/user_guide/system/data-transfer-bundle-products.html#method-2-edit-the-product-data) in onze gebruikersgids uitgeven.
1. Herhaal de importbewerking.

Voor algemene informatie bij de Invoer, zie het [ Invoerende Product van de Bundel ](https://docs.magento.com/m2/ee/user_guide/system/data-transfer-bundle-products.html) in onze gebruikersgids.
