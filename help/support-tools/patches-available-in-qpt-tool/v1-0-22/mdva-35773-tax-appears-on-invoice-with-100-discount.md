---
title: 'MDVA-35773: Belasting verschijnt op factuur met 100% korting'
description: De patch MDVA-35773 verhelpt het probleem waarbij de Grand Total niet als nul wordt weergegeven op de factuur voor bestellingen met een korting van 100%. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 is geïnstalleerd. De patch-id is MDVA-35773. Het probleem is opgelost in Adobe Commerce versie 2.4.3.
exl-id: 895cb7d3-be9f-4864-9658-87ee0471f556
feature: Invoices, Marketing Tools, Orders, Personalization, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-35773: Belasting verschijnt op factuur met 100% korting

De patch MDVA-35773 verhelpt het probleem waarbij de Grand Total niet als nul wordt weergegeven op de factuur voor bestellingen met een korting van 100%. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.2 is geïnstalleerd. De patch-id is MDVA-35773. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.3.6

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.6-2.3.7 en 2.4.1-2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Navigeren naar **Winkels** > **Instellingen** > **Configuratie** > **Verkoop** > **Belasting**.
1. Set **Catalogusprijzen** en **Korting op prijzen toepassen** tot *Inclusief belasting*.
1. Navigeren naar **Winkels** > **Belastingregels** > **Nieuwe belastingregel toevoegen**.
1. Maak een belastingregel (bijvoorbeeld: alle VS met een belastingtarief van 10%) en pas deze toe.
1. Navigeren naar **Marketing** > **Lijnen met winkelprijzen**, en **Nieuwe regel toevoegen**.
1. Een regel maken met een **100% korting voor alle gebruikers**.
1. Maak een orde op Storefront:

   * Kies **Gratis verzending**.
   * Toepassen **Couponcode**.

1. Navigeren naar **Verkoop** > **Orders** en open uw bestelling.
1. Maak een factuur voor de bestelling en open deze.

<u>Verwachte resultaten</u>:

De factuur Eindtotaal = *$ 0,00*.

<u>Werkelijke resultaten</u>:

De factuur Eindtotaal = *belastingbedrag* wordt gemaakt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
