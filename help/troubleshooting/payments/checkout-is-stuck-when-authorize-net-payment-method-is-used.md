---
title: Afhandeling is vastgelopen wanneer de betalingsmethode Authorize.net wordt gebruikt
description: Dit artikel bevat een uitleg en oplossing voor het Adobe Commerce 2.3.X-probleem waarbij het uitchecken vastloopt als Authorize.net wordt gebruikt, met het foutbericht *'Cannot read property 'length' of null'* in het browserconsolelogboek.
exl-id: 01dc1147-4010-4dc5-81f3-3b3015a8c47c
feature: Cache, Checkout, Console, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Afhandeling is vastgelopen wanneer de betalingsmethode Authorize.net wordt gebruikt

Dit artikel bevat een uitleg en oplossing voor het Adobe Commerce 2.3.X-probleem waarbij het afrekenen vastloopt als Authorize.net wordt gebruikt, met het *&#39;Kan eigenschap &#39;length&#39; van null niet lezen* foutbericht in het logboek van de browserconsole.

## Betrokken producten en versies

* Adobe Commerce 2.3.X

>[!NOTE]
>
>De belangrijkste integratie van Adobe Commerce Authorize.Net voor betalingen is afgekeurd sinds 2.3.4 en is volledig verwijderd in 2.4.0. Gebruik een extensie die aan uw behoeften voldoet vanuit de [Adobe Commerce [!DNL Marketplace]](https://commercemarketplace.adobe.com/) in plaats daarvan.

## Probleem

<u>Stappen om te reproduceren</u>

1. Configureer de betalingsmethode Authorize.net in Commerce Admin.
1. Ga naar de winkel.
1. Voeg een product toe aan het winkelwagentje en ga verder met het afrekenen.
1. Kies Authorize.net als betalingsmethode.
1. Klikken **Opdracht plaatsen**.

<u>Verwacht resultaat</u>

Het iframe Authorize.net wordt geladen.

<u>Werkelijk resultaat</u>

Ajax spinner wordt weergegeven en de pagina wordt nooit geladen. De volgende JS-fout wordt weergegeven in het logboek van de browserconsole: *&#39;Uncaught TypeError: Cannot read property &#39;length&#39; of null at b (jstest.authorize.net/v1/AcceptCore.js:1)&#39;)*

## Oorzaak

Één van de gemeenschappelijkste redenen voor deze kwestie is de Openbare Sleutel van de Cliënt die niet in de Authorize.Net configuratie in Commerce Admin wordt gespecificeerd.

## Oplossing

Onder **Winkels** > **Instellingen** > **Configuratie** > **Verkoop** > **Betalingsmethoden** in de **Authorize.net** sectie, controleer of de waarde in **Openbare clientsleutel** veld. Als het leeg is, ga de belangrijkste waarde van uw Authorize.Net handelsrekening in.

Maak de cache schoon door de wijzigingen uit te voeren

```bash
bin/magento cache:clean
```
