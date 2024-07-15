---
title: E-mailadres bestellen dat is verzonden vanaf het e-mailadres van de server
description: Deze artikelen bieden een patch voor het bekende Adobe Commerce-probleem met cloudinfrastructuur 2.2.4 met betrekking tot e-mailberichten voor bestellingen die worden verzonden vanaf het e-mailadres van de server.
exl-id: f32e0c09-e19e-4269-bbba-0533d74a7f49
feature: Communications
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# E-mailadres bestellen dat is verzonden vanaf het e-mailadres van de server

Deze artikelen bieden een patch voor het bekende Adobe Commerce-probleem met cloudinfrastructuur 2.2.4 met betrekking tot e-mailberichten voor bestellingen die worden verzonden vanaf het e-mailadres van de server.

## Probleem

E-mails ter bevestiging van de bestelling worden verzonden vanaf het e-mailadres van de Apache-server. Andere e-mailadressen (wachtwoord vergeten enzovoort) worden verzonden vanaf de geconfigureerde e-mailadressen.

<u> Stappen om </u> te reproduceren:

1. Plaats een orde met **verzend gecontroleerde de bevestiging van de orde** doos.
1. Controleer e-mail.

<u> Verwacht resultaat </u>:

Het e-mailbericht is verzonden vanuit het door Adobe Commerce geconfigureerde verzendadres.

<u> Werkelijk resultaat </u>:

De e-mail is verzonden vanaf het e-mailadres dat is geconfigureerd in de Apache-server die wordt gebruikt.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[Download MDVA-10993\_EE\_2.2.4\_v1.composer.patch](assets/MDVA-10993_EE_2.2.4_v1.composer.patch.zip)

### Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce over wolkeninfrastructuur 2.2.4

De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce on Cloud Infrastructure 2.2.5
* Adobe Commerce on Cloud Infrastructure 2.2.6
* Adobe Commerce on Cloud Infrastructure 2.2.7
* Adobe Commerce on Cloud Infrastructure 2.2.8
* Adobe Commerce op locatie 2.2.4
* Adobe Commerce op locatie 2.2.5
* Adobe Commerce op locatie 2.2.6
* Adobe Commerce op locatie 2.2.7
* Adobe Commerce op locatie 2.2.8
* Adobe Commerce op locatie 2.3.0

## Hoe de pleister aanbrengen

Voor instructies, zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze steunkennisbasis wordt verstrekt.

## Bijgevoegde bestanden
