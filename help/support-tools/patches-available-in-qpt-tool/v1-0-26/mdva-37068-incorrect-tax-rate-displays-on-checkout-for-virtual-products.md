---
title: "MDVA-37068: Onjuiste belasting weergegeven op afhandeling van virtuele producten"
description: De patch MDVA-37068 verhelpt het probleem wanneer op de pagina voor afhandeling een onjuist belastingtarief voor virtuele producten wordt weergegeven. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 is geïnstalleerd. De patch-id is MDVA-37068. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: ef75b41e-e79d-4947-8b74-87966642f808
feature: Cache, Checkout, Orders, Products, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-37068: Onjuiste belasting weergegeven op afhandeling voor virtuele producten

De patch MDVA-37068 verhelpt het probleem wanneer op de pagina voor afhandeling een onjuist belastingtarief voor virtuele producten wordt weergegeven. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 is geïnstalleerd. De patch-id is MDVA-37068. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**
Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met Adobe Commerce-versies:**
Adobe Commerce (alle implementatiemethoden) 2.3.1-2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als de winkelwagentje alleen virtuele producten bevat, wordt op de afhandelingspagina een onjuist BTW-tarief weergegeven.

<u>Vereisten</u>:

1. Twee afzonderlijke belastingtarieven en belastingregels voor twee verschillende landen - bijvoorbeeld 10% en 1%.
1. Maak een virtueel product.
1. Voer opnieuw uit en maak cache schoon.

<u>Stappen om te reproduceren</u>:

1. Maak een klant.
1. Andere facturerings- en verzendadressen toevoegen.
1. Voeg een virtueel product aan de kar toe.
1. Controleer de pagina Winkelwagentje en Afhandeling.

<u>Verwachte resultaten</u>:

De belasting op de pagina Winkelwagentje en Afhandeling is hetzelfde.

<u>Werkelijke resultaten</u>:

De belasting die op de pagina Winkelwagentje en Afhandeling wordt weergegeven, is NIET gelijk.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen afhankelijk van uw implementatiemethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
