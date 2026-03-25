---
title: Adobe Commerce 2.4.0 Braintree Virtual Terminal is beschadigd
description: Dit artikel verstrekt een flard voor de bekende kwestie van Adobe Commerce 2.4.0, waar de Virtuele Eindpagina van Braintree niet de juiste elementen UI of een correct foutenmelding laadt als Braintree niet wordt gevormd.
exl-id: 1d4d762d-2ab3-4752-ad6d-1eb6a179917d
feature: Orders, Payments
role: Developer
source-git-commit: 1dcd003bd9b08741c0fba464f5520797cfaeccbb
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 Braintree Virtual Terminal is beschadigd

Dit artikel verstrekt een flard voor de bekende kwestie van Adobe Commerce 2.4.0, waar de Virtuele Eindpagina van Braintree niet de juiste elementen UI of een correct foutenmelding laadt als Braintree niet wordt gevormd.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.0
* Adobe Commerce over cloudinfrastructuur 2.4.0

## Probleem

### Scenario 1: betalingsmethode Braintree is geconfigureerd

<u> Stappen om te reproduceren:</u>

In Commerce Admin, ga naar **Verkoop** > **Virtuele Terminal van Braintree** ** *

<u> Verwacht resultaat:</u>

De **Virtuele Eind van Braintree {** pagina laadt met juiste UI.

<u> Ware resultaat:</u>

UI van de **Virtuele Eind van Braintree** pagina is gebroken.

### Scenario 2: De betalingsmethode Braintree is geconfigureerd

<u> Stappen om te reproduceren:</u>

In Commerce Admin, ga naar **Verkoop** > **Virtuele Terminal van Braintree** ** *

<u> Verwacht resultaat:</u>

De **Virtuele Eind van Braintree {** pagina laadt met juiste UI en een waarschuwing wordt getoond op de hoogte brengend dat Braintree nog niet wordt gevormd.

<u> Ware resultaat:</u>

UI van de **Virtuele Eindpagina van Braintree** wordt gebroken en geen waarschuwing wordt getoond.

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

Zie [ hoe te om een componentenflard toe te passen die door Adobe ](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) voor instructies wordt verstrekt.

## Bijgevoegde bestanden
