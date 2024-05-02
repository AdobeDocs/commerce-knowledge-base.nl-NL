---
title: Extension Manager geeft geen extensies weer in Adobe Commerce 2.3.x
description: Dit artikel biedt een oplossing voor ontbrekende extensies in de Admin Extension Manager in Adobe Commerce 2.3.x nadat u extensies hebt aangeschaft via de Commerce Marketplace.
exl-id: bed8506d-39b9-449a-891b-466d214a0fe8
feature: Extensions
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Extension Manager geeft geen extensies weer in Adobe Commerce 2.3.x

Dit artikel biedt een oplossing voor ontbrekende extensies in de Admin Extension Manager in Adobe Commerce 2.3.x nadat u extensies hebt aangeschaft via de Commerce Marketplace.

## Betrokken producten en versies

* Adobe Commerce-versie (alle implementatiemethoden) 2.3.x

## Probleem

Wanneer u extensies aanschaft via de Commerce Marketplace, kunt u deze niet installeren met de Adobe Commerce-kernExtension Manager. Wanneer u de toegangstoetsen toevoegt en synchroniseert met de Marketplace, ziet de Extension Manager geen extensies.

De **Workaround** omdat u de opdrachtregel voor de Adobe Commerce-installatie moet gebruiken, zoals in [Algemene CLI-installatie](https://devdocs.magento.com/extensions/install/) in onze ontwikkelaarsdocumentatie.

<u>Stappen om te reproduceren</u>:

1. Een extensie aanschaffen via de Commerce Marketplace.
1. Voeg de toegangstoetsen van uw extensie toe en synchroniseer deze met de Marketplace.
1. Ga naar de sectie Extension Manager van de Admin.

<u>Verwacht resultaat</u>:

De extensie wordt weergegeven in de sectie Extension Manager van Commerce Admin.

<u>Werkelijk resultaat</u>:

**In de sectie Extension Manager van Commerce Admin wordt geen extensie weergegeven, vergelijkbaar met de onderstaande afbeelding:**


![KB-607_Image_1.png](assets/KB-607_Image_1.png)

## Workaround

De opdrachtregel voor Adobe Commerce-installatie gebruiken, zoals wordt getoond in [Algemene CLI-installatie](https://devdocs.magento.com/extensions/install/) in onze ontwikkelaarsdocumentatie.
