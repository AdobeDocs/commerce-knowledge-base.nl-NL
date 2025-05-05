---
title: Kan entiteit Adobe Commerce-backend niet opslaan
description: Dit artikel biedt een oplossing als u een entiteit niet kunt opslaan in de Adobe Commerce-backend. Bijvoorbeeld, wanneer u niet een specifieke "cart_price"regel kunt uitgeven en bewaren.
exl-id: e45dc88a-2da0-4524-bd61-6634cfebb169
feature: Admin Workspace, Marketing Tools
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Kan entiteit Adobe Commerce-backend niet opslaan

Dit artikel biedt een oplossing als u een entiteit niet kunt opslaan in de Adobe Commerce-backend. Wanneer u bijvoorbeeld een specifieke `cart_price` -regel niet kunt bewerken en opslaan.

## Betrokken producten en versies

Dit probleem kan van invloed zijn op alle Adobe Commerce-versies waarvoor Max Session Size is geconfigureerd. Dit werd toegevoegd die van Magento Open Source 2.3.7-p1 en Adobe handel (alle plaatsingsmethodes) 2.4.3 begon.


## Probleem

Wanneer u uw winkel opnieuw probeert te configureren, wordt de pagina opnieuw geladen en worden de wijzigingen niet opgeslagen. Een bericht kan worden weergegeven in `var/log/system.log` :

*[2021-11-27 00 :30: 52 ] report.WARNING: De grootte van de zitting van 418056 overtrof toegestane zittingsmaximum grootte van 256000. [][]*

<u> Stappen om </u> te reproduceren:

Een voorbeeld van opslagconfiguratie die niet wordt opgeslagen:

1. Selecteer een regel in de opslag van Adobe Commerce in Productie > **Marketing** > **de prijsregels van de Kar**.
1. Kies een regel en reeks aan *Inactief* en bewaar de verandering.

<u> Verwacht resultaat </u>:

De regel is ingesteld op inactief.

<u> Werkelijk resultaat </u>:

* Pagina wordt opnieuw geladen zonder enig bericht.
* De regel is nog steeds ingesteld op actief.

## Oorzaak

Dit probleem houdt verband met de nieuwe functionaliteit die onlangs is geïntroduceerd en die invloed heeft gehad op de maximale sessiegrootte. Zie [ beheer van de Zitting ](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/security/security-session-management) in onze ontwikkelaarsdocumentatie.

## Oplossing

Verhoog de &quot;Max waarde van de Grootte van de Zitting&quot;in (**opslag** > **Configuratie** > **Geavanceerd** > **Systeem** > **Veiligheid** > Max de Grootte van de Zitting).

## Gerelateerde lezing

* [ het In de handel brengen Menu ](https://experienceleague.adobe.com/nl/docs/commerce-admin/marketing/marketing-menu) in onze gebruikersgids.
