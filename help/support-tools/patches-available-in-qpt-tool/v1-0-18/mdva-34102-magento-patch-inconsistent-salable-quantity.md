---
title: "MDVA-34102: inconsistente verkoopbare hoeveelheid"
description: De patch MDVA-34102 lost het probleem op waarbij de hoeveelheid standaardvoorraad nul is voor uitgeschakelde producten op het Productraster en Productpagina's bewerken in Admin. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 is geïnstalleerd. De patch-id is MDVA-34102. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.
exl-id: cb1d4689-c122-4afd-8597-b2627027aaf3
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-34102: inconsistente verkoopbare hoeveelheid

De patch MDVA-34102 lost het probleem op waarbij de hoeveelheid standaardvoorraad nul is voor uitgeschakelde producten op het Productraster en Productpagina&#39;s bewerken in Admin. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 is geïnstalleerd. De patch-id is MDVA-34102. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.0-2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Twee websites instellen met winkels en winkelweergaven.
1. Maak een extra bron en voorraad.
1. Voeg een eenvoudig product toe:
   * Set **Product inschakelen** = *Nee*.
   * Twee bronnen toewijzen met **Status van bronitem** = *In voorraad* met een hoeveelheid groter dan nul (voorbeeld: **standaardvoorraad** = *123* en **VK-voorraad** = *123*).
1. Sla het product op.
1. Controleer de **Aankoopbare hoeveelheid product** tab.

<u>Verwachte resultaten</u>:

Zowel de standaardvoorraad als de Britse voorraad = *123.*

De hoeveelheid standaardvoorraad wordt correct weergegeven voor uitgeschakelde producten op de pagina&#39;s Productraster en Product bewerken in Admin.

<u>Werkelijke resultaten</u>:

De standaardvoorraad = *0* en het Britse bestand = *123.*

De hoeveelheid standaardvoorraad is nul voor uitgeschakelde producten op het productraster en de pagina&#39;s Product bewerken in de Admin.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
