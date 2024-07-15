---
title: 'MDVA-36286: De voorproef van de Bouwer van de pagina breekt als SKU in verschillende categorieën plaatst'
description: Met de MDVA-36286-patch wordt het probleem opgelost waarbij de voorvertoning van de producten van de widget Page Builder wordt afgebroken als dezelfde SKU een andere positie in subcategorieën heeft. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.23 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: 0f7d2506-569a-4b70-82bf-0f153014c48a
feature: CMS, Categories, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-36286: De voorproef van de Bouwer van de pagina breekt als SKU in verschillende categorieën plaatst

Met de MDVA-36286-patch wordt het probleem opgelost waarbij de voorvertoning van de producten van de widget Page Builder wordt afgebroken als dezelfde SKU een andere positie in subcategorieën heeft. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.23 geïnstalleerd is. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over wolkeninfrastructuur 2.3.6

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.6 - 2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om te reproduceren:</u>

1. Maak een categorie met een paar producten.
   ![ products_magento_ordered.png ](/help/support-tools/patches-available-in-qpt-tool/assets/products_magento_ordered.png)
1. Maak een subcategorie met dezelfde producten maar met verschillende posities.
   ![ products_magento_different_position.png ](/help/support-tools/patches-available-in-qpt-tool/assets/products_magento_different_position.png)
1. Bewerk de inhoud van een CMS-pagina om een productwidget toe te voegen via Page Builder. (Selecteer de bovenliggende categorie hierboven).
   ![ cms_page_magento.png ](/help/support-tools/patches-available-in-qpt-tool/assets/cms_page_magento.png)
1. Sla het bestand op en wacht tot de voorvertoning van de inhoud.

<u> Verwachte resultaten:</u>

In de voorvertoning van de inhoud wordt de productwidget weergegeven.

<u> Ware resultaten:</u>

Foutweergaven:

*wij spijt, is een fout voorgekomen terwijl het produceren van deze inhoud.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
