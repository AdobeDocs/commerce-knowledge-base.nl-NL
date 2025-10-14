---
title: Conflicterende componentafhankelijkheden
description: Dit artikel biedt een oplossing voor conflicterende componentafhankelijkheden. Wanneer u probeert Adobe Commerce in te stellen of bij te werken met de wizard Web Setup, wordt het foutbericht *"We hebben conflicterende componentafhankelijkheden"* Composer gevonden.
exl-id: 782049c4-b6e1-4ead-a00f-80d2aa8475c9
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# Conflicterende componentafhankelijkheden

Dit artikel biedt een oplossing voor conflicterende componentafhankelijkheden. Wanneer het proberen om Adobe Commerce op te zetten of bij te werken gebruikend de Tovenaar van de Opstelling van het Web, ziet u *&quot;wij ontdekten conflicterende componentengebiedsdelen&quot;* de foutenmelding van Composer.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.2.x, 2.3.x
* Adobe Commerce op cloud-infrastructuur 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x


## Probleem {#issue}

Een conflicterend foutbericht over componentafhankelijkheden dat lijkt op het volgende (de namen en versies van het pakket variëren in feite):

```bash
We found conflicting component dependencies.
You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
We have detected conflicts with the following packages:
- magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

## Oorzaak

Dit bericht wordt weergegeven als Composer niet kan bepalen welke componenten moeten worden geïnstalleerd of bijgewerkt.

## Oplossing

Twee hoofdscenario&#39;s kunnen tot conflicterende componentengebiedsdelen leiden. Klik op uw scenario om het oplossen van problemenstappen te krijgen.

* [Adobe Commerce upgraden](#upgrading-magento)
* [Incompatibiliteit met modules van derden:](#incompatibility-third-party-modules)
   * [Adobe Commerce (alle implementatietypen)](#magento-commerce-magento-commerce-cloud)
   * [Magento Open Source](#opensource)

## Adobe Commerce upgraden {#upgrading-magento}

Als u Adobe Commerce upgradet op een cloudinfrastructuur, probeert u het volgende om conflicterende componentafhankelijkheden op te lossen:

* Controleer de toetsen die worden gebruikt voor een upgrade. Worden de sleutels geproduceerd van de correcte e-mailrekening?
* Controleer de machtigingen en zorg ervoor dat deze voldoen aan de upgradevereisten voor het Magento. Het overzicht van de Verbetering van het Magento [&#x200B; > Controlelijst van de Update en van de Verbetering > de Toestemmingen van het Systeem van het Dossier &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/upgrade-guide/prepare/prerequisites#verify-file-system-permissions) in onze ontwikkelaarsdocumentatie.

## Incompatibiliteit met modules van derden: {#incompatibility-third-party-modules}

Conflicterende componentengebiedsdelen kunnen ook door derdemodules worden veroorzaakt die van vroegere componenten van Commerce dan degenen afhangen u hebt geïnstalleerd. Probeer het volgende:

1. In het voorafgaande [&#x200B; voorbeeld &#x200B;](#issue), kan het geïnstalleerde pakket magento/sample-data versie 0.74.0-beta15 niet aan 1.0.0-bèta worden bevorderd. 0,74,0-bèta15 kan echter worden geüpgraded naar 0,74,0-bèta16 (of andere). Bewerk `composer.json` om deze wijzigingen aan te brengen. Doorgaans worden de versies die uw project aanvraagt, gedefinieerd in de eigenschap `require` of `require-dev` van het object in dat JSON-bestand. Afhankelijk van de opties van de meegeleverde pakketversies, kunnen ze een specifieke versie of een beperking opgeven. Voor algemene begeleiding op hoe te om composer te gebruiken, als u op onze wolkeninfrastructuur bent, kunt u naar [&#x200B; Wolk voor Adobe Commerce > Technologieën en Vereisten > Composer &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/overview#files) in onze ontwikkelaarsdocumentatie verwijzen. Als u op Adobe Commerce op-gebouw bent, verwijs naar [&#x200B; Adobe Commerce > de Gids van de Installatie > installeer Adobe Commerce Gebruikend Composer &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/composer).
1. Probeer nu de gereedheidscontrole. Herzie [&#x200B; het Overzicht van de Verbetering van Adobe Commerce > stel de Manager van de Module > Stap 1 Controle van de Bereidheid &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/upgrade-guide/overview) in onze ontwikkelaarsdocumentatie in werking.
1. Als de gereedheidscontrole met een ander de mislukkingsbericht van de de gebiedscontrole van de Component ontbreekt, klik op de volgende verbindingen afhankelijk van of u [&#x200B; Adobe Commerce &#x200B;](#magento-commerce-magento-commerce-cloud) of [&#x200B; Magento Open Source &#x200B;](#opensource) gebruikt om verdere het oplossen van problemenstappen te krijgen.

## Adobe Commerce {#magento-commerce-magento-commerce-cloud}

1. Vraag de ontwikkelaar van de extensie om hulp. U vindt hun contactgegevens op de pagina waarop u de extensie hebt aangeschaft op de Commerce Marketplace. Zoek de **Verkoper van het Contact** knoop die op het juiste paneel wordt getoond. Alle Commerce-ontwikkelaars moeten een gebruikers- en installatiegids leveren wanneer ze een extensie publiceren op Marketplace. U kunt beide vinden op de rechterkant van hun landingspagina.
1. Als u geen reactie van de verkoper in een redelijke hoeveelheid tijd ontvangt, gelieve [&#x200B; de Steun van de Marketplace &#x200B;](mailto:commercemarketplacesupport@adobe.com) te contacteren zodat wij hen op hun verplichtingen van de klantensteun kunnen herinneren.

## Magento Open Source {#opensource}

Vraag hulp bij [&#x200B; ons belangrijkste forum &#x200B;](https://community.magento.com/) of [&#x200B; contact een Partner van Adobe Commerce &#x200B;](https://magento.com/find-a-partner) die in Open kwesties van Source bijstaat.
