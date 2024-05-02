---
title: 'ACSD-53750: fout met "Broken pipe of closed connection" tijdens multi-threaded catalog_product_price redex'
description: Pas de ACSD-53750-patch toe om het Adobe Commerce-probleem op te lossen waarbij een fout *Broken pipe of closed connection* optreedt tijdens multi-threaded catalog_product_price redex.
feature: Products
role: Admin, Developer
exl-id: afb30384-74e7-4857-9aff-8e99f5abc309
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-53750: *Gebroken pijp of gesloten verbinding* fout tijdens multi-threaded `catalog_product_price` hergroeperen

De ACSD-53750-patch verhelpt het probleem waarbij een *Gebroken pijp of gesloten verbinding* fout treedt op tijdens multi-threaded `catalog_product_price` redex. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.37 is geïnstalleerd. De patch-id is ACSD-53750. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

*Gebroken pijp of gesloten verbinding* fout treedt op tijdens multi-threaded `catalog_product_price` redex.

<u>Stappen om te reproduceren</u>:

1. Vorm RabbitMq.
1. Voorbeeldgegevens genereren met behulp van de bijlage `small.xml` bestand.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** en instellen **[!UICONTROL Stock/Source reindex strategy]** = **[!UICONTROL Asynchronous]**.
1. Stel de dimensiemodus in voor indexen die dat ondersteunen. bijv. `catalog_product_price_website_and_customer_group` of `customer_group`.

   ```
   bin/magento indexer:set-dimensions-mode catalog_product_price customer_group
   ```

1. Herstellen van indexen uitvoeren voor `catalog_product_price`.

   ```
   bin/magento indexer:reset catalog_product_price
   ```

1. Stel de indexeerder voor het terugstellen indexeerder in werking gebruikend veelvoudige draden.

   ```
   MAGE_INDEXER_THREADS_COUNT=10 bin/magento indexer:reindex catalog_product_price
   ```

<u>Verwachte resultaten</u>:

Er treden geen fouten op.

<u>Werkelijke resultaten</u>:

De volgende fout wordt veroorzaakt door een verbinding AMQP: *Gebroken pijp of gesloten verbinding*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
