---
title: 'MDVA-43491: basislabel voor afbeelding wordt niet bijgewerkt wanneer het wordt geïmporteerd via CSV'
description: De patch MDVA-43491 verhelpt het probleem waarbij het label "base_image_label" niet wordt bijgewerkt wanneer het wordt geïmporteerd via een CSV-bestand voor een website met meerdere winkels. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 is geïnstalleerd. De patch-id is MDVA-43491. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: d744423a-f582-4410-8d66-861229cce1b5
feature: Data Import/Export
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-43491: basislabel voor afbeelding wordt niet bijgewerkt wanneer het wordt geïmporteerd via CSV

De MDVA-43491-patch verhelpt het probleem waarbij de `base_image_label` wordt niet bijgewerkt wanneer geïmporteerd via een CSV-bestand voor een website met meerdere winkels. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 is geïnstalleerd. De patch-id is MDVA-43491. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De `base_image_label` wordt niet bijgewerkt wanneer geïmporteerd met een CSV-bestand voor een website met meerdere opslaglocaties.

<u>Vereisten</u>:

Een of meer bestaande niet-standaardwebsites, winkels en winkelweergaven.

<u>Stappen om te reproduceren</u>:

1. Maak een nieuw product.

   * Upload een afbeelding.
   * Wijs het product toe aan de nieuwe websites.

1. Exporteer het product als CSV.
1. Werk de `base_image_label` voor elke archiefweergave door de standaardrij van het CSV-bestand te dupliceren.
1. Het CSV-bestand importeren. De labels voor elke winkel worden op de juiste wijze bijgewerkt. Dit kan worden geverifieerd onder het tabblad **Afbeeldingen en video&#39;s** op de productbewerkingspagina.
1. Exporteer het CSV-bestand opnieuw en werk de `base_image_label` kolom met verschillende waarden.
1. Importeer het CSV-bestand opnieuw.
1. Open het product in de Admin en controleer of het label voor elke winkelweergave is bijgewerkt.

<u>Verwachte resultaten</u>:

Alt Text (afbeeldingslabel) wordt bijgewerkt met de opslagspecifieke waarde volgens het CSV-bestand.

<u>Werkelijke resultaten</u>:

Alt-tekst (afbeeldingslabel) wordt niet bijgewerkt met de `base_image_label` in het CSV-bestand.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
