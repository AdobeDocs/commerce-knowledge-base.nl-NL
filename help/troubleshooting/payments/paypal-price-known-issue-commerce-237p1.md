---
title: 'Bekende uitgave bij ''Adobe Commerce 2.3.7-p1: totaal van verouderde bestellingen voor PayPal'''
description: 'Dit artikel biedt een patch voor een bekend probleem in Adobe Commerce 2.3.7-p1: wanneer je PayPal-afhandeling meerdere keren gebruikt, krijgen klanten het eerder bestelde product in winkelwagentje in plaats van het nieuwe product dat ze proberen te bestellen.'
exl-id: ceb8f7ad-0cf7-4d42-aded-25d1dd947f5b
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Bekende uitgave van Adobe Commerce 2.3.7-p1: totaal van verouderde bestellingen voor PayPal

Dit artikel bevat een patch voor een bekend probleem in Adobe Commerce 2.3.7-p1: wanneer je PayPal-afhandeling meerdere keren gebruikt, krijgen klanten het eerder bestelde product in winkelwagentje in plaats van het nieuwe product dat ze proberen te bestellen.
U kunt de patch downloaden vanuit dit artikel en deze is ook beschikbaar via het QPT (Quality Patches Tool).

## Betrokken versies

* Adobe Commerce (alle implementatieopties) 2.3.7-p1
* Magento Open Source 2.3.7-p1

## Probleem

Wanneer u een bestelling plaatst met de PayPal Express-betalingsmethode, wordt het eerder bestelde gekochte product toegevoegd aan de bestelling in plaats van aan de eigenlijke bestelling.

<u> Stappen om te reproduceren:</u>

1. Voeg op de winkelvoorzijde elk product aan de winkelwagentje toe (product A, prijs $50).
1. Klik op de koppeling Kar om de kar te openen.
1. Klik de **PayPal knoop van de Controle**.
1. Gebruik uw PayPal-gegevens om u aan te melden bij PayPal en de betaling te verzenden.
1. Beëindig de plaatsing van de bestelling aan de kant van de winkel.
1. Ga terug naar de catalogus en voeg een ander product (product B, prijs $100) aan de kar toe.
1. Klik op de koppeling Kar om de kar te openen.
1. Klik de **PayPal knoop van de Controle**.

<u> Ware resultaat:</u>

De productprijs in de winkelwagen is $50 in plaats van $100.<br/>
Aan de zijde van de winkel bevat de bestelling product A in plaats van product B.

<u> Verwacht resultaat:</u>

Product B wordt toegevoegd aan de bestelling.

## Oplossing

Pas de patch toe die in dit artikel is opgenomen.

## Reparatie

Gebruik de volgende verbinding om een .zip dossier te downloaden dat het flard bevat: [ MC42674-composer.patch.zip ](assets/MC42674-composer.patch.zip).

### Compatibele Adobe Commerce-versies

* Adobe Commerce (alle implementatieopties) 2.3.7-p1

## De pleisters aanbrengen

1. Pak het gedownloade .zip-bestand uit.
1. Zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor verdere instructies wordt verstrekt.
