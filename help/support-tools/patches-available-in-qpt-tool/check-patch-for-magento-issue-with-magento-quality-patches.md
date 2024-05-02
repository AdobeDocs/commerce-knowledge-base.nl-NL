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

* Adobe Commerce op locatie, alle [ondersteunde versies](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce op cloudinfrastructuur, alle [ondersteunde versies](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Wat is het gereedschap Kwaliteitspatches

De [Gereedschap Kwaliteitspatches](https://github.com/magento/quality-patches) (QPT) zijn afzonderlijke patches die door Adobe en de Magento Open Source gemeenschap zijn ontwikkeld.

Zo kunt u:

* past meegeleverde kwaliteitspatches toe op het pakket
* eerder toegepaste patches herstellen
* Bekijk de algemene informatie over kwaliteitspatches die beschikbaar zijn voor de geïnstalleerde versie van Adobe Commerce.

Hier is een voorbeeld van de statuslijst u kunt krijgen om de beschikbare flarden te bekijken:

![Magento_patches_list](assets/status_table.png)

Het gereedschap is bedoeld om u in staat te stellen zelf te dienen met patches voor problemen die u kunt ervaren met Adobe Commerce, of om eenvoudig patches toe te passen die worden voorgesteld door Adobe Commerce-ondersteuning.

>[!NOTE]
>
>QPT is alleen voor kwaliteitspatches. Beveiligingspatches zijn beschikbaar in het dialoogvenster [Magento Security Center](https://magento.com/security/patches).

## Patches beschikbaar in het gereedschap Kwaliteitspatches

Zie [Gereedschap Kwaliteitspatches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie voor de lijst van beschikbare flarden.

## Het gereedschap Kwaliteitspatches installeren en gebruiken

De installatie- en gebruiksopdrachten verschillen voor Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur, omdat voor cloud het QPT-pakket is opgenomen in het ece-tools-pakket.

### QPT voor Adobe Commerce installeren en gebruiken op locatie

Zie [Software Update Guide > Patching](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie voor meer informatie over het installeren en gebruiken van QPT voor het toepassen en herstellen van patches.

### QPT voor Adobe Commerce installeren en gebruiken op cloudinfrastructuur

Zie [Cloud voor Adobe Commerce > Patches toepassen](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie voor meer informatie over het installeren en gebruiken van QPT voor het toepassen en herstellen van patches op Adobe Commerce op cloudinfrastructuur.

## Gerelateerde lezing

* [Opmerkingen bij de release Quality Patches Tool](https://devdocs.magento.com/quality-patches/release-notes.html) in onze ontwikkelaarsdocumentatie.
* [Hoe worden door Adobe geleverde componentpatches toegepast](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze kennisbasis voor ondersteuning.
