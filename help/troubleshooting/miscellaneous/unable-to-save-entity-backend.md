---
title: Kan entiteit Adobe Commerce-backend niet opslaan
description: Dit artikel biedt een oplossing als u een entiteit niet kunt opslaan in de Adobe Commerce-backend. Bijvoorbeeld, wanneer u niet een specifieke "cart_price"regel kunt uitgeven en bewaren.
exl-id: e45dc88a-2da0-4524-bd61-6634cfebb169
feature: Admin Workspace, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Kan entiteit Adobe Commerce-backend niet opslaan

Dit artikel biedt een oplossing als u een entiteit niet kunt opslaan in de Adobe Commerce-backend. Als u bijvoorbeeld een bepaalde `cart_price` regel.

## Betrokken producten en versies

Dit probleem kan van invloed zijn op alle Adobe Commerce-versies waarvoor Max Session Size is geconfigureerd. Dit werd toegevoegd die van Magento Open Source 2.3.7-p1 en Adobe handel (alle plaatsingsmethodes) 2.4.3 begon.


## Probleem

Wanneer u uw winkel opnieuw probeert te configureren, wordt de pagina opnieuw geladen en worden de wijzigingen niet opgeslagen. Een bericht is zichtbaar in `var/log/system.log`:

*[11-27 00:30:52] report.WARNING: De sessiegrootte van 418056 overschrijdt de toegestane sessiegrootte van maximaal 256000. [][]*

<u>Stappen om te reproduceren</u>:

Een voorbeeld van opslagconfiguratie die niet wordt opgeslagen:

1. Selecteer een regel in de Adobe Commerce Store in Production > **Marketing** > **Prijsregels voor winkelwagentjes**.
1. Kies een regel en stel deze in op *Inactief* en sla de wijziging op.

<u>Verwacht resultaat</u>:

De regel is ingesteld op inactief.

<u>Werkelijk resultaat</u>:

* Pagina wordt opnieuw geladen zonder enig bericht.
* De regel is nog steeds ingesteld op actief.

## Oorzaak

Dit probleem houdt verband met de nieuwe functionaliteit die onlangs is geïntroduceerd en die invloed heeft gehad op de maximale sessiegrootte. Zie [Sessiebeheer](https://docs.magento.com/user-guide/stores/security-session-management.html) in onze ontwikkelaarsdocumentatie.

## Oplossing

Verhoog de waarde Max Sessiegrootte in (**Winkels** > **Configuratie** > **Geavanceerd** > **Systeem** > **Beveiliging** > Maximale sessiegrootte).

## Gerelateerde lezing

* [Marketingmenu](https://docs.magento.com/user-guide/marketing/marketing-menu.html) in onze gebruikershandleiding.
