---
title: "MDVA-33704 patch: In-store pickup does not display"
description: Met de MDVA-33704-patch wordt het probleem opgelost waarbij producten met de optie Ophalen in de winkel niet als een verzendmethode worden weergegeven.
exl-id: 2c5c7627-5d2e-44d2-9579-314dbd31ee8b
feature: Shipping/Delivery
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# MDVA-33704-patch: Ophalen in winkel wordt niet weergegeven

Met de MDVA-33704-patch wordt het probleem opgelost waarbij producten met de optie Ophalen in de winkel niet als een verzendmethode worden weergegeven.

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-33704. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce op cloudinfrastructuur 2.4.0-p1

**Compatibel met Adobe Commerce-versies:** Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.4.0-2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Vereiste</u>:<br>

**Winkel kiezen** enabled

<u>Stappen om te reproduceren</u>:

1. Voeg een product toe aan de kar.
1. Ga naar Afhandeling.
1. Voeg verzendgegevens toe en kies een andere verzendmethode dan het ophalen in de winkel.
1. Selecteren **Doorgaan met betaling**, maar ga dan niet verder naar de betalingspagina.
1. Ga in plaats daarvan terug naar de **Contact en verzending** sectie.
1. Selecteren **Ophalen**.
1. Selecteren **Winkel** en **Klik om te betalen**.
1. Je verzendadres wordt automatisch ingevoerd als factuuradres.
1. Vernieuw de webpagina.

<u>Verwachte resultaten</u>:

De optie Ophalen in de winkel wordt als een verzendmethode weergegeven, zoals u had verwacht.

<u>Werkelijke resultaten</u>:

De optie Ophalen in winkel wordt niet weergegeven als verzendmethode.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
