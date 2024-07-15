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

De ACSD-45241-patch verhelpt het probleem waarbij de voorraadhoeveelheid van het virtuele product onjuist wordt berekend nadat een creditmemo is gemaakt. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 geïnstalleerd is. De patch-id is ACSD-45241. De kwestie is opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De voorraadhoeveelheid voor een virtueel product wordt verkeerd berekend na het creëren van een creditnota.

<u> Stappen om </u> te reproduceren:

1. Een configureerbaar product maken met een virtueel product als een onderliggend product in Commerce Admin.
1. Zorg ervoor dat beide in stap 1 gemaakte producten in voorraad zijn.
1. Markeer de hoeveelheid voor het virtuele product dat in stap 1 wordt gemaakt als 100 en houd de verkoopbare hoeveelheid ook 100.
1. Voeg het product toe aan het winkelwagentje.
1. Plaats een bestelling bij het virtuele product dat u in stap 1 hebt gemaakt.
1. De status van de bestelling behouden als &quot;In behandeling&quot;. De betaling hoeft niet te worden verwerkt.
1. `order_created` -record gemaakt in `inventory_reservation` . De hoeveelheid van het virtuele product is 100 en de hoeveelheid die kan worden verkocht is 99.
1. Open de orde en ga naar **Factuur** > **voorleggen Factuur**.
1. `invoice_created` -record gemaakt in `inventory_reservation` . De hoeveelheid van het virtuele product is nu 99 en de verkoopbare hoeveelheid is ook 99.
1. Creeer een creditmemo zonder **Terugkeer aan Voorraad te selecteren**.

<u> Verwachte resultaten </u>:

Er wordt geen nieuwe record gemaakt in `inventory_reservation` en de voorraadhoeveelheid voor het virtuele product blijft ongewijzigd.

<u> Ware resultaten </u>:

Er wordt een `creditmemo_created` -record gemaakt in `inventory_reservation` en de voorraadhoeveelheid van het virtuele product wordt aangepast aan 98 met een verkoopbare hoeveelheid als 99.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
