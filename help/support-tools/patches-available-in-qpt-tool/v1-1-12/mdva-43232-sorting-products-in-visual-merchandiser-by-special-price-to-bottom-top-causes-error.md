---
title: 'MDVA-43232: Het sorteren van producten in visuele handelaar door Speciale Prijs aan Bovenkant (of Onderkant) veroorzaakt een fout'
description: De patch MDVA-43232 verhelpt het probleem dat het sorteren van producten in visuele merchandiser door Special Price to Top (of Bottom) een fout veroorzaakt bij het opslaan van de categorie. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-43232. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: e958a219-5e93-4ae4-94cb-f478f82ad060
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-43232: Het sorteren van producten in visuele handelaar door Speciale Prijs aan Hoogste (of Onder) veroorzaakt een fout

De patch MDVA-43232 verhelpt het probleem dat het sorteren van producten in visuele merchandiser door Special Price to Top (of Bottom) een fout veroorzaakt bij het opslaan van de categorie. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-43232. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.4 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als producten in visuele handelaren worden gesorteerd op Speciale prijs naar Boven (of Onder), treedt een fout op bij het opslaan van de categorie.

<u>Stappen om te reproduceren</u>:

1. Controleer of er twee websites zijn.
1. Navigeren naar **Winkels** > **Configuratie** > **Catalogus** > **Prijs** en stel Catalog Price Scope = Website in.
1. Opnieuw navigeren naar **Winkels** > **Configuratie** > **Catalogus** > **Visual Merchandiser** > **Zichtbare kenmerken voor categorieregels** > en voeg Speciale prijs toe.
1. Maak een eenvoudig product en wijs de producten toe aan beide websites.
1. Voeg een speciale prijs toe aan het standaardbereik van het product.
1. Schakel over naar het bereik van de andere winkel en overschrijf zowel de prijs als de speciale prijs van dat product.
1. Doe een `catalog_product_price` redex.
1. Ga naar **Catalogus** > **Categorieën** en maak een nieuwe categorie.
1. Voeg een categorieregel toe aan filterproducten met een speciale prijs.
1. Sla de categorie op.
1. Stel onder de sectie Producten in categorie Sorteervolgorde = Speciale prijs boven (of Onder) in.
1. Sla de rubriek opnieuw op.

<u>Verwachte resultaten</u>:

De categorie wordt zonder fouten opgeslagen.

<u>Werkelijke resultaten</u>:

Er wordt een uitzondering gegenereerd:

```php
[2022-02-07T05:58:46.297621+00:00] report.CRITICAL: Exception: Item (Magento\Catalog\Model\Product\Interceptor) with the same ID "1" already exists. in /lib/internal/Magento/Framework/Data/Collection.php:407
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
