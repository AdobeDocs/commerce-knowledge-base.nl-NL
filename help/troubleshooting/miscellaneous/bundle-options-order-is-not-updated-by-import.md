---
title: Volgorde van bundelopties wordt niet bijgewerkt door importeren
description: Dit artikel biedt een oplossing voor het probleem wanneer de opties voor het bundelproduct na het importeren van producten uit een CSV-bestand in een andere volgorde worden weergegeven dan in het importbestand.
exl-id: 7f7bf782-4b35-4067-aa94-417097079f1f
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

1. Importeer het dossier gebruikend de [&#x200B; functionaliteit van de Invoer &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/data-transfer/import/data-import).
1. Open de productpagina van de bundel.

<u> Verwachte resultaten </u>:

De volgorde van opties is gelijk aan die in het CSV-bestand.

<u> Ware resultaten </u>:

De volgorde van opties verschilt van die in het CSV-bestand.

## Oorzaak

De positie van de opties is niet expliciet gedeclareerd.

## Oplossing

1. Declareer expliciet een positie voor elke optie in de parameter `position` van de kolom `bundle_values` in het .csv-bestand. Voor gedetailleerde instructies, zie [&#x200B; de Gegevens van het Product &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/data-transfer/examples/data-transfer-bundle-products#method-2-edit-the-product-data) in onze gebruikersgids uitgeven.
1. Herhaal de importbewerking.

Voor algemene informatie bij de Invoer, zie het [&#x200B; Invoerende Product van de Bundel &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/data-transfer/examples/data-transfer-bundle-products) in onze gebruikersgids.
