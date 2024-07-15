---
title: "Adobe Commerce 2.4.0 B2B: onjuiste logica voor inkooporders wanneer korting verlopen is"
description: Dit artikel biedt een patch voor de bekende uitgave van een inkooporderkorting (PO) die niet wordt toegepast in Adobe Commerce 2.4.0 B2B. Als de PO met een kortingscode werd geplaatst die verliep terwijl PO in het goedkeuringsproces was, weerspiegelt de goedgekeurde orde niet de korting.
exl-id: 3ef41655-c31e-4e9c-8985-fa1b4fd53170
feature: B2B, Orders, Payments, Personalization, Purchase Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B: onjuiste logica voor inkooporders bij verlopen korting

Dit artikel biedt een patch voor de bekende uitgave van een inkooporderkorting (PO) die niet wordt toegepast in Adobe Commerce 2.4.0 B2B. Als de PO met een kortingscode werd geplaatst die verliep terwijl PO in het goedkeuringsproces was, weerspiegelt de goedgekeurde orde niet de korting.

## Betrokken producten en versies

* Adobe Commerce over cloudinfrastructuur 2.4.0
* Adobe Commerce op locatie 2.4.0

## Probleem

<u> Eerste vereisten </u>: een kortingscoupon wordt gecreeerd, en de goedkeuringsregels die POs verhinderen automatisch worden verwerkt bestaan.

<u> Stappen om te reproduceren:</u>

1. Plaats een PO met een toegepaste korting.
1. Deactiveer de kortingscoupon.
1. P.O. goedkeuren als manager.
1. Controleer de volgorde die u als resultaat hebt gemaakt.

<u> Verwacht resultaat:</u>

De orde wordt gecreeerd met een gedisconteerd totaal.

<u> Ware resultaat:</u>

Voor het volledige bedrag wordt een bestelling gemaakt.

## Oplossing

Pas de patch toe die in dit artikel is opgenomen.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[B2B-709-composer.patch](assets/B2B-709-composer.patch.zip)

Het flard is ook beschikbaar voor download in zowel, `.git` als `.composer`, formaten op [ de Downloads van Adobe Commerce ](https://magento.com/tech-resources/download) pagina, onder **Patches** in de linkerkolomnavigatie. Zoeken naar XXX-patch.

## Hoe de pleister aanbrengen

Zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze basis van steunkennis voor instructies wordt verstrekt.
