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

MDVA-31343 patch verhelpt het probleem waarbij de toegewezen hoofdtekst-CSS-klasse voor de layout voor een categorie wordt verwijderd tijdens de geplande update. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 geïnstalleerd is. Het probleem zal volgens planning worden opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Lay-outhoofdklasse wordt verwijderd uit de categorie na de geplande update.

<u> Stappen om </u> te reproduceren:

1. Maak een categorie in Commerce Admin.
1. Plaats **Lay-out** = *Categorie - Volledige breedte* in de **sectie van het Ontwerp**.
1. Sla de categorie op.
1. Ga naar voorpagina van categorie. In de paginabron wordt het

   ```css
   page-layout-category-full-width
   ```

   CSS-klasse.
1. Onder **CATALOG** > **Categorie**, klik **Nieuwe Update van het Programma** in de *Geplande sectie van Veranderingen* voor de nieuwe categorie.
1. Wacht tot de geplande update start, voer de cache voor uitsnijden en leegmaken uit.
1. Ga naar de categoriepagina op de voorzijde en inspecteer de paginabron.

<u> Verwachte resultaten </u>:

In de hoofdtekst van de pagina ziet u de

```css
page-layout-category-full-width
```

CSS-klasse.

<u> Ware resultaten </u>:

In de hoofdtekst van de pagina ziet u de

```css
page-layout-2columns-left
```

CSS-klasse; dit is de standaardklasse voor de categoriepagina.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
