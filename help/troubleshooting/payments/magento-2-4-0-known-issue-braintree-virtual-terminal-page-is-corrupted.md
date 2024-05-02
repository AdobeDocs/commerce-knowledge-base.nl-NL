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

<u>Stappen om te reproduceren:</u>

Ga in Commerce Admin naar **Verkoop** > **Virtuele terminal voor Braintree** . ** **

<u>Verwacht resultaat:</u>

De **Virtuele terminal voor Braintree** pagina wordt geladen met de juiste interface.

<u>Werkelijk resultaat:</u>

De gebruikersinterface van de **Virtuele terminal voor Braintree** pagina is verbroken.

### Scenario 2: betalingsmethode voor Braintree is geconfigureerd

<u>Stappen om te reproduceren:</u>

Ga in Commerce Admin naar **Verkoop** > **Virtuele terminal voor Braintree** . ** **

<u>Verwacht resultaat:</u>

De **Virtuele terminal voor Braintree** pagina wordt geladen met juiste interface en er wordt een waarschuwing weergegeven met de melding dat de Braintree nog niet is geconfigureerd.

<u>Werkelijk resultaat:</u>

De gebruikersinterface van de **Virtuele terminal voor Braintree** pagina is verbroken en er wordt geen waarschuwing weergegeven.

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

Zie [Hoe een door Adobe geleverde componentpleister aanbrengen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies.

## Bijgevoegde bestanden
