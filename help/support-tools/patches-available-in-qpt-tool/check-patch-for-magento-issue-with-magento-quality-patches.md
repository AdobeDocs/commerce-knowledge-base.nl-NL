---
title: Patch controleren voor Adobe Commerce-probleem met het gereedschap Kwaliteitspatches
description: In dit artikel vindt u een overzicht van het gereedschap Kwaliteitspatches (QPT) en koppelingen naar bronnen waarin wordt uitgelegd hoe u het gereedschap kunt gebruiken.
exl-id: 43393708-3939-449f-a764-b2ac6326165f
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Patch controleren voor Adobe Commerce-probleem met het gereedschap Kwaliteitspatches

In dit artikel vindt u een overzicht van het gereedschap Kwaliteitspatches (QPT) en koppelingen naar bronnen waarin wordt uitgelegd hoe u het gereedschap kunt gebruiken.

## Betrokken producten en versies

* Adobe Commerce op-gebouw, alle [ gesteunde versies ](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce op wolkeninfrastructuur, alle [ gesteunde versies ](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Wat is het gereedschap Kwaliteitspatches

Het [ Hulpmiddel van de Patches van de Kwaliteit ](https://github.com/magento/quality-patches) (QPT) zijn individuele die flarden door Adobe en de gemeenschap van de Magento Open Source worden ontwikkeld.

Zo kunt u:

* past meegeleverde kwaliteitspatches toe op het pakket
* eerder toegepaste patches herstellen
* Bekijk de algemene informatie over kwaliteitspatches die beschikbaar zijn voor de geïnstalleerde versie van Adobe Commerce.

Hier is een voorbeeld van de statuslijst u kunt krijgen om de beschikbare flarden te bekijken:

![ Magento_patches_list ](assets/status_table.png)

Het gereedschap is bedoeld om u in staat te stellen zelf te dienen met patches voor problemen die u kunt ervaren met Adobe Commerce, of om eenvoudig patches toe te passen die worden voorgesteld door Adobe Commerce-ondersteuning.

>[!NOTE]
>
>QPT is alleen voor kwaliteitspatches. De flarden van de veiligheid zijn beschikbaar in het [ Centrum van de Veiligheid van de Magento ](https://magento.com/security/patches).

## Patches beschikbaar in het gereedschap Kwaliteitspatches

Gelieve te verwijzen naar [ Hulpmiddel van de Patches van de Kwaliteit ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie voor de lijst van beschikbare flarden.

## Het gereedschap Kwaliteitspatches installeren en gebruiken

De installatie- en gebruiksopdrachten verschillen voor Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur, omdat voor cloud het QPT-pakket is opgenomen in het ece-tools-pakket.

### QPT voor Adobe Commerce installeren en gebruiken op locatie

Gelieve te verwijzen naar [ Gids van de Update van de Software > het Patching ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie voor details op hoe te om QPT voor het toepassen van en het terugkeren van flarden te installeren en te gebruiken.

### QPT voor Adobe Commerce installeren en gebruiken op cloudinfrastructuur

Gelieve te verwijzen naar [ Wolk voor Adobe Commerce > pas flarden ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie voor details op om QPT voor het toepassen en het terugkeren van flarden op Adobe Commerce op wolkeninfrastructuur te installeren en te gebruiken.

## Gerelateerde lezing

* [ de versienota&#39;s van het Hulpmiddel van de Patches van de Kwaliteit ](https://devdocs.magento.com/quality-patches/release-notes.html) in onze ontwikkelaarsdocumentatie.
* [ hoe te om componentenflarden toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze steunkennisbasis worden verstrekt.
