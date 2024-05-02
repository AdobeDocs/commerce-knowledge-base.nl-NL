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

De MDVA-34695-patch lost het probleem op waarbij producten en categorieën niet worden weergegeven in het categorienet in Admin. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 is geïnstalleerd. De patch-id is MDVA-34695. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.3.4

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.0-2.4.0-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Negatieve waarden voor `children_count` worden weergegeven in de database nadat categorieën zijn verwijderd.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de beheerder-back-end.
1. Navigeren naar **Catalogus > Categorieën**.
1. Klikken **Subcategorie toevoegen**.
1. Set **categorienaam** = *Bovenliggend element 1* en vervolgens Opslaan.
1. Klikken **Subcategorie toevoegen**.
1. Set **categorienaam** = *Kind 1* en vervolgens Opslaan.
1. Klikken **Subcategorie toevoegen**.
1. Set **categorienaam** = *Kind 2* en vervolgens Opslaan.
1. Klikken **Subcategorie toevoegen**.
1. Set **categorienaam** = *Kind 3* en vervolgens Opslaan. Op dit punt moet deze categorie een niveau hebben = *5*.
1. Klik op de knop **Kind 1** categorie.
1. Verwijder de categorie.

<u>Verwachte resultaten</u>:

In het raster voor categorieën worden de producten en categorieën weergegeven, zoals u had verwacht.

<u>Werkelijke resultaten</u>:

Het categorieraster is leeg. Controleer de `catalog_category_entity` in de database. Let op: `children_count` negatief werd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
