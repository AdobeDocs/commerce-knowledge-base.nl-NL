---
title: "MDVA-34695: Producten en categorieën die niet worden weergegeven"
description: De MDVA-34695-patch lost het probleem op waarbij producten en categorieën niet worden weergegeven in het categorienet in Admin. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 is geïnstalleerd. De patch-id is MDVA-34695. Het probleem is opgelost in Adobe Commerce versie 2.4.3.
exl-id: 0c2e50c1-648b-480a-a768-72af721950d8
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-34695: Producten en categorieën die niet worden weergegeven

De MDVA-34695-patch lost het probleem op waarbij producten en categorieën niet worden weergegeven in het categorienet in Admin. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 geïnstalleerd is. De patch-id is MDVA-34695. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over wolkeninfrastructuur 2.3.4

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.0-2.4.0-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Negatieve waarden voor `children_count` worden in de database weergegeven nadat categorieën zijn verwijderd.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij de beheerder-back-end.
1. Navigeer aan **Catalogus > Categorieën**.
1. Klik **toevoegen Subcategory**.
1. Plaats **categorienaam** = *Ouder 1*, dan sparen.
1. Klik **toevoegen Subcategory**.
1. Plaats **categorienaam** = *Kind 1*, dan sparen.
1. Klik **toevoegen Subcategory**.
1. Plaats **categorienaam** = *Kind 2*, dan sparen.
1. Klik **toevoegen Subcategory**.
1. Plaats **categorienaam** = *Kind 3*, dan sparen. Op dit punt, zou deze categorie een niveau moeten hebben = *5*.
1. Klik op **Kind 1** categorie.
1. Verwijder de categorie.

<u> Verwachte resultaten </u>:

In het raster voor categorieën worden de producten en categorieën weergegeven, zoals u had verwacht.

<u> Ware resultaten </u>:

Het categorieraster is leeg. Controleer de `catalog_category_entity` tabel in de database. `children_count` werd negatief.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
