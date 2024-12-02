---
title: 'MDVA-40550: Producten die aan de voorzijde ontbreken na redexering'
description: Met de MDVA-40550-patch wordt het probleem opgelost waarbij opnieuw indexeren leidt tot enkele of alle ontbrekende producten in de winkelcategorieën. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 is geïnstalleerd. De patch-id is MDVA-40550. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 0aca6eb2-6eb2-4ac4-8ae1-052f671c14e5
feature: Categories, Console, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MDVA-40550: Producten die aan de voorzijde ontbreken na redexering

Met de MDVA-40550-patch wordt het probleem opgelost waarbij opnieuw indexeren leidt tot enkele of alle ontbrekende producten in de winkelcategorieën. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 geïnstalleerd is. De patch-id is MDVA-40550. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

1. Maak een product.
1. De indexen van de schakelaar aan **Update door programma**.
   * Wijs het product toe aan een categorie.
1. Schakel Xdebug in en maak Xdebug-onderbrekingspunten in `\Magento\Indexer\Model\Indexer::reindexAll` en `\Magento\Indexer\Model\IndexMutex::execute` .
1. Voer a **volledige herdex** van `catalog_category_product` met het bevel in werking:

   ```bash
   bin/magento indexer:reindex catalog_category_product
   ```

   * Wacht tot de uitvoering wordt gestopt op het onderbrekingspunt `\Magento\Indexer\Model\Indexer::reindexAll`.

1. In een andere console, stel a **gedeeltelijke herdex** parallel met het bevel in werking:

   ```bash
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Wacht tot de uitvoering wordt gestopt op het onderbrekingspunt `\Magento\Indexer\Model\IndexMutex::execute`. De `catalog_category_product` indexer wordt vergrendeld.
1. Hervat de uitvoering van de volledige redex van `catalog_category_product` en wacht op een vergrendelingstijd (60 seconden).

<u> Verwachte resultaten </u>:

Geen foutberichten in console.

<u> Ware resultaten </u>:

De volgende fout treedt op:

*Kon geen slot voor index verwerven: catalog_category_product.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in onze ontwikkelaarsdocumentatie.
