---
title: Modules ontbreken in Adobe Commerce 2.4.4
description: Dit artikel biedt een oplossing voor het probleem wanneer modules uit eerdere Adobe Commerce-versies niet aanwezig zijn in 2.4.4.
exl-id: c0335b66-803b-44d7-b966-7d60a5f21d8d
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Modules ontbreken in Adobe Commerce 2.4.4

Dit artikel biedt een oplossing voor het geval modules die zijn opgenomen in eerdere Adobe Commerce-versies niet aanwezig zijn in 2.4.4.

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden) alle  [ondersteunde versies](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Probleem

U kunt geen module van derden installeren of u hebt ontdekt dat sommige van de kerngebundelde extensies niet aanwezig zijn wanneer u een upgrade naar Adobe Commerce 2.4.4 uitvoert. Dit zou slechts uit het installeren van een derdemodule moeten voortvloeien die één van de gebundelde uitbreidingen vereist die uit Adobe Commerce 2.4.4 worden verwijderd of als het project sommige functionaliteit van één van de verwijderde modules gebruikt.

* Scenario 1: Het project heeft één van de kern gebundelde functionaliteit van de module gebruikt. De gebruikte gebundelde module is niet inbegrepen in Adobe Commerce 2.4.4. Nadat u de upgrade naar Adobe Commerce 2.4.4 hebt voltooid, realiseert u zich dat de module en de bijbehorende functionaliteit ontbreken.

* Scenario 2: U hebt een module die in uw huidig project wordt geïnstalleerd die een gebiedsdeel op één van de verwijderde gebundelde modules heeft.

Dit wordt verwacht aangezien de leverancier-Gebundelde Uitbreidingen uit de codebasis van Adobe Commerce 2.4.4 zijn verwijderd.

## Oplossing

De officiële extensies afzonderlijk installeren/aanschaffen. Deze zijn beschikbaar op [Commerce Marketplace](https://marketplace.magento.com/extensions.html).

## Gerelateerde lezing

[Door leveranciers gebundelde extensies](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-4.html?#vendor-bundled-extensions) in Adobe Commerce Documentation > Release Information > Adobe Commerce 2.4.4 Release notes.
