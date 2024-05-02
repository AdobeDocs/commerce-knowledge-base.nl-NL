---
title: "MDVA-32133 patch: page builder does not load media gallery"
description: De MDVA-32133-patch lost het probleem op waarbij de medialerie niet is geladen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 is geïnstalleerd. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.
exl-id: c0ce799d-b452-4044-9635-4218db3904ef
feature: CMS, Media, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-32133-patch: page builder laadt geen mediagalerie

De MDVA-32133-patch lost het probleem op waarbij de medialerie niet is geladen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 is geïnstalleerd. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over cloudinfrastructuur 2.4.0

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce over wolkeninfrastructuur en Adobe Commerce op locatie 2.4.0 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Hiermee wordt het probleem verholpen waarbij de ordergeschiedenis zeer langzaam wordt geladen of helemaal niet.

<u>Stappen om te reproduceren</u>:

1. Geselecteerde cms-pagina bewerken.
1. Inhoud uitvouwen en klikken **Bewerken met Page Builder**.
1. Media uitbreiden. Sleep de afbeelding naar het gebied Rij.
1. Klikken **Selecteren in galerie**.
1. U kunt zich afmelden en zich dan aanmelden via een ander venster.

<u>Verwachte resultaten</u>:

De mediagalerie wordt geladen.

<u>Werkelijke resultaten</u>:

De mediagalerie is niet geladen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
