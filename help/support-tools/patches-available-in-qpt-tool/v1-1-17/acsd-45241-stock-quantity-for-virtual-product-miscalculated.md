---
title: "ACSD-45241: Onjuist berekende voorraadhoeveelheid van een virtueel product"
description: De ACSD-45241-patch verhelpt het probleem waarbij de voorraadhoeveelheid van het virtuele product onjuist wordt berekend nadat een creditmemo is gemaakt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 is geïnstalleerd. De patch-id is ACSD-45241. De kwestie is opgelost in Adobe Commerce 2.4.4.
exl-id: 4be97da9-d399-419a-816e-cf65f15cc3be
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# ACSD-45241: Onjuist berekende voorraad van virtueel product

De ACSD-45241-patch verhelpt het probleem waarbij de voorraadhoeveelheid van het virtuele product onjuist wordt berekend nadat een creditmemo is gemaakt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 is geïnstalleerd. De patch-id is ACSD-45241. De kwestie is opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De voorraadhoeveelheid voor een virtueel product wordt verkeerd berekend na het creëren van een creditnota.

<u>Stappen om te reproduceren</u>:

1. Een configureerbaar product maken met een virtueel product als een onderliggend product in Commerce Admin.
1. Zorg ervoor dat beide in stap 1 gemaakte producten in voorraad zijn.
1. Markeer de hoeveelheid voor het virtuele product dat in stap 1 wordt gemaakt als 100 en houd de verkoopbare hoeveelheid ook 100.
1. Voeg het product toe aan het winkelwagentje.
1. Plaats een bestelling bij het virtuele product dat u in stap 1 hebt gemaakt.
1. De status van de bestelling behouden als &quot;In behandeling&quot;. De betaling hoeft niet te worden verwerkt.
1. `order_created` record gemaakt in `inventory_reservation`. De hoeveelheid van het virtuele product is 100 en de hoeveelheid die kan worden verkocht is 99.
1. Open de bestelling en ga naar **Factuur** > **Factuur verzenden**.
1. `invoice_created` record gemaakt in `inventory_reservation`. De hoeveelheid van het virtuele product is nu 99 en de verkoopbare hoeveelheid is ook 99.
1. Een creditmemo maken zonder te selecteren **Terug naar voorraad**.

<u>Verwachte resultaten</u>:

Er wordt geen nieuwe record gemaakt in `inventory_reservation`en de voorraadhoeveelheid voor het virtuele product ongewijzigd blijft.

<u>Werkelijke resultaten</u>:

A `creditmemo_created` record wordt gemaakt in `inventory_reservation`, en de hoeveelheid van de virtuele productvoorraad wordt aangepast aan 98 met verkoopbare hoeveelheid als 99.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
