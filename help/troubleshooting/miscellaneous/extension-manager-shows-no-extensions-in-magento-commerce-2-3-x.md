---
title: Extension Manager geeft geen extensies weer in Adobe Commerce 2.3.x
description: Dit artikel biedt een oplossing voor ontbrekende extensies in de Admin Extension Manager in Adobe Commerce 2.3.x nadat u extensies hebt aangeschaft via de Commerce Marketplace.
exl-id: bed8506d-39b9-449a-891b-466d214a0fe8
feature: Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

De **Oplossing** voor de kwestie moet de installatie van de bevellijnAdobe Commerce zoals aangetoond in [&#x200B; Algemene installatie CLI &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/tutorials/extensions) in onze ontwikkelaarsdocumentatie gebruiken.

<u> Stappen om </u> te reproduceren:

1. Een extensie aanschaffen via de Commerce Marketplace.
1. Voeg de toegangstoetsen van uw extensie toe en synchroniseer deze met de Marketplace.
1. Ga naar de sectie Extension Manager van de Admin.

<u> Verwacht resultaat </u>:

De extensie wordt weergegeven in de sectie Extension Manager van Commerce Admin.

<u> Werkelijk resultaat </u>:

**geen uitbreiding verschijnt op de sectie van de Extension Manager van Commerce Admin, gelijkend op het hieronder beeld:**


![&#x200B; KB-607_Image_1.png &#x200B;](assets/KB-607_Image_1.png)

## Workaround

Gebruik de installatie van Adobe Commerce van de bevellijn zoals aangetoond in [&#x200B; Algemene installatie CLI &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/tutorials/extensions) in onze ontwikkelaarsdocumentatie.
