---
title: '"MDVA-39181: producten van categorie "niet gedefinieerd in regel"'
description: Met de MDVA-39181-patch wordt het probleem opgelost waarbij gerelateerde productregels producten uit een categorie weergeven die niet in de regel is gedefinieerd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 is geïnstalleerd. De patch-id is MDVA-39181. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: b6364d1c-2480-483a-9a83-ac91feeb14b9
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39181: producten uit categorie &quot;niet gedefinieerd&quot; in regel worden in de desbetreffende productregels vermeld

Met de MDVA-39181-patch wordt het probleem opgelost waarbij gerelateerde productregels producten uit een categorie weergeven die niet in de regel is gedefinieerd. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 is geïnstalleerd. De patch-id is MDVA-39181. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De verwante productregels tonen producten uit categorieën die niet in de regel worden bepaald.

<u>Vereisten</u>:

Voorbeeldgegevens installeren.

<u>Stappen om te reproduceren</u>:

1. Een kenmerkmerk maken en toevoegen aan de **Tops-kenmerkset**.
1. Kies **Josie**, **Augusta**, en **Ingrid** colbertjassen voor de Brand Kitty **Vrouwen** > **Tops** > **Jasjes, categorie**.
1. Kies **Beaumont**, **Hyperion**, en **Kenobi** colbertjassen voor de Brand Kitty **Mannen** > **Tops** > **Jasje, categorie**.
1. Een verwant product maken met:

   ```markdown
   Apply To: Related Products
   Customer Segments: All
   ```

   * Producten afstemmen:

   ```markdown
   If ALL of these conditions are TRUE
     Category is {}
     Brand is {}
   ```

   * Te tonen producten:

   ```markdown
   If ALL of these conditions are TRUE
      Product Category is the same as Matched Product Category
      Product brand is Matched Product Brand
   ```

1. Open SKU WJ04 van het vooreind en controleer verwante producten.
1. Categorie-id bijwerken vanuit **Vrouwen** > **Tops** > **Jasjes** indien dit anders is.

<u>Verwachte resultaten</u>:

Alleen producten van hetzelfde merk en dezelfde kindercategorie worden in verwante producten vermeld.

<u>Werkelijke resultaten</u>:

Verwante producten worden van hetzelfde merk getoond, maar van een willekeurige oudercategorie.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
