---
title: 'MDVA-31343 patch: planning update verwijdert body class for category'
description: MDVA-31343 patch verhelpt het probleem waarbij de toegewezen hoofdtekst-CSS-klasse voor de layout voor een categorie wordt verwijderd tijdens de geplande update. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd. Het probleem zal volgens planning worden opgelost in Adobe Commerce 2.4.2.
exl-id: 50dbff01-cb77-4cac-b90e-5c4b06f5e4e7
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-31343 patch: planning update verwijdert body class voor categorie

MDVA-31343 patch verhelpt het probleem waarbij de toegewezen hoofdtekst-CSS-klasse voor de layout voor een categorie wordt verwijderd tijdens de geplande update. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd. Het probleem zal volgens planning worden opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Lay-outhoofdklasse wordt verwijderd uit de categorie na de geplande update.

<u>Stappen om te reproduceren</u>:

1. Maak een categorie in Commerce Admin.
1. Set **Layout** = *Categorie — Volledige breedte* in de **Ontwerp** sectie.
1. Sla de categorie op.
1. Ga naar voorpagina van categorie. In de paginabron wordt het

   ```css
   page-layout-category-full-width
   ```

   CSS-klasse.
1. Onder **CATALOGUS** > **Categorie**, klikt u op **Nieuwe update plannen** in de *Geplande wijzigingen* voor de nieuwe categorie.
1. Wacht tot de geplande update start, voer de cache voor uitsnijden en leegmaken uit.
1. Ga naar de categoriepagina op de voorzijde en inspecteer de paginabron.

<u>Verwachte resultaten</u>:

In de hoofdtekst van de pagina ziet u de

```css
page-layout-category-full-width
```

CSS-klasse.

<u>Werkelijke resultaten</u>:

In de hoofdtekst van de pagina ziet u de

```css
page-layout-2columns-left
```

CSS-klasse; dit is de standaardklasse voor de categoriepagina.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
