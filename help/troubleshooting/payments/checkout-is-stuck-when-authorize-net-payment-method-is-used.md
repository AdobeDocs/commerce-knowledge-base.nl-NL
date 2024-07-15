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

Dit artikel verstrekt een verklaring en moeilijke situatie voor de Adobe Commerce 2.3.X kwestie waar het uitchecken wordt geplakt als Authorize.net wordt gebruikt, met *&quot;Kan bezit &quot;lengte&quot;van ongeldig&quot;niet lezen* foutenmelding in het logboek van de browser console.

## Betrokken producten en versies

* Adobe Commerce 2.3.X

>[!NOTE]
>
>De belangrijkste integratie van Adobe Commerce Authorize.Net voor betalingen is afgekeurd sinds 2.3.4 en is volledig verwijderd in 2.4.0. Gebruik een uitbreiding die uw behoeften van [ Adobe Commerce  [!DNL Marketplace] ](https://commercemarketplace.adobe.com/) in plaats daarvan aanpast.

## Probleem

<u> Stappen om te reproduceren </u>

1. Configureer de betalingsmethode Authorize.net in Commerce Admin.
1. Ga naar de winkel.
1. Voeg een product toe aan het winkelwagentje en ga verder met het afrekenen.
1. Kies Authorize.net als betalingsmethode.
1. Klik **de Orde van de Plaats**.

<u> Verwacht resultaat </u>

Het iframe Authorize.net wordt geladen.

<u> Werkelijk resultaat </u>

Ajax spinner wordt weergegeven en de pagina wordt nooit geladen. De volgende JS-fout wordt weergegeven in het browserconsolelogboek: *&#39;Uncaught TypeError: Cannot read property &#39;length&#39; of null at b (jstest.authorize.net/v1/AcceptCore.js:1)&#39;*

## Oorzaak

Één van de gemeenschappelijkste redenen voor deze kwestie is de Openbare Sleutel van de Cliënt die niet in de Authorize.Net configuratie in Commerce Admin wordt gespecificeerd.

## Oplossing

Onder **Opslag** > **Montages** > **Configuratie** > **Verkoop** > **de Methoden van de Betaling**, in de **Authorize.net** sectie, controleer als de waarde in het **Openbare Sleutel van de Cliënt** gebied wordt gespecificeerd. Als het leeg is, ga de belangrijkste waarde van uw Authorize.Net handelsrekening in.

Maak de cache schoon door de wijzigingen uit te voeren

```bash
bin/magento cache:clean
```
