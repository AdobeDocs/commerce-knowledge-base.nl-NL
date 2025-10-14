---
title: Adobe Commerce 2.4.0 Braintree Virtual Terminal is beschadigd
description: Dit artikel verstrekt een flard voor de bekende kwestie van Adobe Commerce 2.4.0, waar de Virtuele Eindpagina van de Braintree niet de juiste elementen UI of een correct foutenmelding laadt als de Braintree niet wordt gevormd.
exl-id: 1d4d762d-2ab3-4752-ad6d-1eb6a179917d
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 Braintree Virtual Terminal is beschadigd

Dit artikel verstrekt een flard voor de bekende kwestie van Adobe Commerce 2.4.0, waar de Virtuele Eindpagina van de Braintree niet de juiste elementen UI of een correct foutenmelding laadt als de Braintree niet wordt gevormd.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.0
* Adobe Commerce over cloudinfrastructuur 2.4.0

## Probleem

### Scenario 1: betalingsmethode voor Braintree is geconfigureerd

<u> Stappen om te reproduceren:</u>

In Commerce Admin, ga naar **Verkoop** > **de Virtuele Terminal van de Braintree** ** *

<u> Verwacht resultaat:</u>

De **Virtuele Eind van de Braintree &lbrace;** pagina laadt met juiste UI.

<u> Ware resultaat:</u>

UI van de **Virtuele Eind van de Braintree** pagina is gebroken.

### Scenario 2: betalingsmethode voor Braintree is geconfigureerd

<u> Stappen om te reproduceren:</u>

In Commerce Admin, ga naar **Verkoop** > **de Virtuele Terminal van de Braintree** ** *

<u> Verwacht resultaat:</u>

De **Virtuele Eind van de Braintree &lbrace;** pagina laadt met juiste UI en een waarschuwing wordt getoond informerend dat de Braintree nog niet wordt gevormd.

<u> Ware resultaat:</u>

UI van de **Virtuele Eind van de Braintree** pagina wordt gebroken en geen waarschuwing wordt getoond.

## Oplossing

Pas de patch toe die in dit artikel is opgenomen.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[BUNDLE-2670-composer.patch](assets/BUNDLE-2670-composer.patch.zip)

### Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce over cloudinfrastructuur 2.4.0
* Adobe Commerce op locatie 2.4.0

## Hoe de pleister aanbrengen

Zie [&#x200B; hoe te om een componentenflard toe te passen die door Adobe &#x200B;](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies wordt verstrekt.

## Bijgevoegde bestanden
