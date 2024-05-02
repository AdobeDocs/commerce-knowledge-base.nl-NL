---
title: "MDVA-40550: Producten die aan de voorzijde ontbreken na herindexering"
description: Met de MDVA-40550-patch wordt het probleem opgelost waarbij opnieuw indexeren leidt tot enkele of alle ontbrekende producten in de winkelcategorieën. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 is geïnstalleerd. De patch-id is MDVA-40550. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 0aca6eb2-6eb2-4ac4-8ae1-052f671c14e5
feature: Categories, Console, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MDVA-40550: Producten die aan de voorzijde ontbreken na redexering

Met de MDVA-40550-patch wordt het probleem opgelost waarbij opnieuw indexeren leidt tot enkele of alle ontbrekende producten in de winkelcategorieën. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 is geïnstalleerd. De patch-id is MDVA-40550. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Maak een product.
1. Indexeerders schakelen naar **Bijwerken volgens schema**.
   * Wijs het product toe aan een categorie.
1. Xdebug inschakelen en Xdebug-onderbrekingspunt instellen in `\Magento\Indexer\Model\Indexer::reindexAll` en `\Magento\Indexer\Model\IndexMutex::execute`.
1. Een **volledige redex** van `catalog_category_product` met de opdracht:

   ```bash
   bin/magento indexer:reindex catalog_category_product
   ```

   * Wacht tot de uitvoering is gestopt op het onderbrekingspunt `\Magento\Indexer\Model\Indexer::reindexAll`.

1. Voer in een andere console een **gedeeltelijke reïndex** parallel met de opdracht:

   ```bash
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Wacht tot de uitvoering is gestopt op het onderbrekingspunt `\Magento\Indexer\Model\IndexMutex::execute`. Het zal de `catalog_category_product` indexeerprogramma.
1. Hervat de uitvoering van de volledige herdex van `catalog_category_product` en wacht op een vergrendelingstime-out (60 seconden).

<u>Verwachte resultaten</u>:

Geen foutberichten in console.

<u>Werkelijke resultaten</u>:

De volgende fout treedt op:

*Kan vergrendeling niet verkrijgen voor index: catalog_category_product.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
