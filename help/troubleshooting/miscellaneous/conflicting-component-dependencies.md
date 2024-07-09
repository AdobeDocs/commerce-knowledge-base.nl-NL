---
title: Conflicterende componentafhankelijkheden
description: Dit artikel biedt een oplossing voor conflicterende componentafhankelijkheden. Wanneer u probeert Adobe Commerce in te stellen of bij te werken met de wizard Web Setup, wordt het foutbericht *"We hebben conflicterende componentafhankelijkheden"* Composer gevonden.
exl-id: 782049c4-b6e1-4ead-a00f-80d2aa8475c9
feature: Configuration
role: Developer
source-git-commit: 8f0f7412e75e07a22e66236b88c095c698dbf23e
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# Conflicterende componentafhankelijkheden

Dit artikel biedt een oplossing voor conflicterende componentafhankelijkheden. Wanneer u probeert Adobe Commerce in te stellen of bij te werken met de wizard Web Setup, ziet u de *&quot;We hebben conflicterende componentafhankelijkheden gevonden&quot;* Foutbericht van composer.

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
* Controleer de machtigingen en zorg ervoor dat deze voldoen aan de upgradevereisten voor het Magento. Controleren [Overzicht van upgrade van Magento > Controlelijst voor bijwerken en bijwerken > Bestandssysteemmachtigingen](https://devdocs.magento.com/guides/v2.3/comp-mgr/prereq/prereq_compman-checklist.html#perms) in onze ontwikkelaarsdocumentatie.

## Incompatibiliteit met modules van derden: {#incompatibility-third-party-modules}

Conflicterende componentengebiedsdelen kunnen ook door derdemodules worden veroorzaakt die van vroegere componenten van Commerce dan degenen afhangen u hebt geïnstalleerd. Probeer het volgende:

1. In het voorgaande [voorbeeld](#issue)kan het geïnstalleerde pakket magento/sample-data versie 0.74.0-beta15 niet worden bijgewerkt naar 1.0.0-bèta. 0,74,0-bèta15 kan echter worden geüpgraded naar 0,74,0-bèta16 (of andere). Bewerken `composer.json` om deze wijzigingen aan te brengen. De versies die uw project aanvraagt, worden meestal gedefinieerd in het dialoogvenster `require` of `require-dev` eigenschap van het object in dat JSON-bestand. Afhankelijk van de opties van de meegeleverde pakketversies, kunnen ze een specifieke versie of een beperking opgeven. Voor algemene richtlijnen over het gebruik van composer kunt u, als u zich op onze cloudinfrastructuur bevindt, verwijzen naar [Cloud voor Adobe Commerce > Technologieën en vereisten > Composer](https://devdocs.magento.com/cloud/reference/cloud-composer.html#files) in onze ontwikkelaarsdocumentatie. Als je in Adobe Commerce op locatie bent, raadpleeg dan [Adobe Commerce > Installation Guide > Install Adobe Commerce Using the Composer](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html) .
1. Probeer nu de gereedheidscontrole. Controleren [Adobe Commerce Upgrade Overview > Voer Module Manager > Step 1 Readiness Check uit](https://devdocs.magento.com/guides/v2.3/comp-mgr/module-man/compman-readiness.html) in onze ontwikkelaarsdocumentatie.
1. Als de gereedheidscontrole mislukt bij een ander foutbericht voor een componentafhankelijkheidscontrole, klikt u op de volgende koppelingen, afhankelijk van of u het programma gebruikt [Adobe Commerce](#magento-commerce-magento-commerce-cloud) of [Magento Open Source](#opensource) om verdere het oplossen van problemenstappen te krijgen.

## Adobe Commerce {#magento-commerce-magento-commerce-cloud}

1. Vraag de ontwikkelaar van de extensie om hulp. U vindt hun contactgegevens op de pagina waarop u de extensie hebt aangeschaft op de Commerce Marketplace. Zoek naar **Contact opnemen met verkoper** weergegeven in het rechterdeelvenster. Alle Commerce-ontwikkelaars moeten een gebruikers- en installatiegids leveren wanneer ze een extensie publiceren op Marketplace. U kunt beide vinden op de rechterkant van hun landingspagina.
1. Als je binnen een redelijke termijn geen antwoord van de verkoper ontvangt, [Contact opnemen met de ondersteuning van Marktplaats](mailto:commercemarketplacesupport@adobe.com) zodat wij hen kunnen herinneren aan hun verplichtingen inzake klantenondersteuning.

## Magento Open Source {#opensource}

Hulp aanvragen bij [ons belangrijkste forum](https://community.magento.com/) of [contact opnemen met een Adobe Commerce-partner](https://magento.com/find-a-partner) dat helpt bij Open Source-problemen.
