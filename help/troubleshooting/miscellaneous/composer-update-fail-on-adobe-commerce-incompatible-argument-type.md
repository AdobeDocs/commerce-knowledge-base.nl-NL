---
title: 'Composer-update mislukt op Adobe Commerce: niet-compatibel argumenttype'
description: Dit artikel verstrekt een oplossing voor wanneer de plaatsing wordt geplakt omdat er een kwestie met codecompilatie is. Deze kwestie wordt veroorzaakt door een nieuwe versie van symfony/consoleafhankelijkheid (4.4.27, 4.4.28).
exl-id: ba2dd229-29f6-43e2-9467-8bd1bf59e6ef
feature: Console
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Composer-update mislukt op Adobe Commerce: niet-compatibel argumenttype

>[!NOTE]
>
>Dit probleem is nu opgelost in de meest recente symfony versie 4.4.29.

Dit artikel verstrekt een oplossing voor wanneer de plaatsing wordt geplakt omdat er een kwestie met codecompilatie is. Deze kwestie wordt veroorzaakt door een nieuwe versie van symfony/consoleafhankelijkheid (4.4.27, 4.4.28).

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden) en Magento Open Source:
   * 2.4.0, 2.4.0-p1, 2.4.1, 2.4.1-p1, 2.4.2, 2.4.2-p1, 2.4.2-p2, 2.4.3
   * 2.3.5, 2.3.5-p1, 2.3.5-p2, 2.3.6, 2.3.6-p1, 2.3.7, 2.3.7-p1
* symfonie-/consoleafhankelijkheid (4.4.27, 4.4.28).

## Probleem

Een nieuwe versie van symfony/consoleafhankelijkheid (4.4.27, 4.4.28) veroorzaakt het proces van de gebiedsdeelcompilatie om te ontbreken.

<u> Stappen om </u> te reproduceren:

Wanneer u Adobe Commerce installeert of bijwerkt of een composer-update uitvoert, mislukt de uitvoering met het volgende foutbericht:
*Niet-compatibel argumenttype: Vereist type: int. Werkelijk type: tekenreeks*

## Oorzaak

Dit probleem wordt veroorzaakt door de incompatibiliteit van de kerncode van Adobe Commerce met de meest recente &#39;symfony/console&#39;-afhankelijkheid die in de versies 4.4.27 en 4.4.28 is uitgebracht.

## Oplossing

Het probleem wordt automatisch opgelost wanneer een nieuwe symfony/console-versie 4.2.29 wordt uitgebracht (verwacht in augustus 2021).

**hoe te op Adobe Commerce op-gebouw te bevestigen:**

Adobe Commerce op locatie 2.4.x

Voer het volgende bevel in CLI/Terminal in werking:

``composer require symfony/console:">=4.4.0 <4.4.27 || ~4.4.29"``

Alle 2.3.5+ Adobe Commerce op-gebouw verkopers zouden het volgende CLI bevel moeten in werking stellen:

``composer require symfony/console:"~4.1.0||~4.2.0||~4.3.0||>=4.4.0 <4.4.27 || ~4.4.29"``

**hoe te op Adobe Commerce op wolkeninfrastructuur te bevestigen:**

Voer de bovenstaande opdrachten uit of voer een upgrade uit naar de nieuwste versie van de ECE-gereedschappen (ece-tools: 2002.1.7), die op donderdag 29 juli beschikbaar zal zijn. Voor stappen, verwijs naar [ Wolk voor Adobe Commerce > update knoop-hulpmiddelen versie ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package) in onze ontwikkelaarsdocumentatie.

De volledige oplossing wordt vrijgegeven in Adobe Commerce (alle implementatiemethoden) 2.4.4.

## Gerelateerde lezing

* Github: [ 2021-07-27 de update van Composer Incompatibel argumenttype: Vereist type: int. Werkelijk type: tekenreeks ](https://github.com/magento/magento2/issues/33595)
