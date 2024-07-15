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

# ACSD-53750: *Gebroken pijp of gesloten verbinding* fout tijdens multi-threaded `catalog_product_price` herdex

Het ACSD-53750 flard bevestigt de kwestie waar a *Gebroken pijp of gesloten verbinding* fout tijdens multi-threaded `catalog_product_price` herdex voorkomt. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.37 wordt geïnstalleerd. De patch-id is ACSD-53750. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

*Gebroken pijp of gesloten verbinding* fout komt tijdens multi-threaded `catalog_product_price` herdex voor.

<u> Stappen om </u> te reproduceren:

1. Vorm RabbitMq.
1. Voorbeeldgegevens genereren met het bijgevoegde `small.xml` -bestand.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** en stel **[!UICONTROL Stock/Source reindex strategy]** = **[!UICONTROL Asynchronous]** in.
1. Stel de dimensiemodus in voor indexen die dat ondersteunen. Bijvoorbeeld `catalog_product_price_website_and_customer_group` of `customer_group` .

   ```
   bin/magento indexer:set-dimensions-mode catalog_product_price customer_group
   ```

1. Herstel van indexen voor `catalog_product_price` uitvoeren.

   ```
   bin/magento indexer:reset catalog_product_price
   ```

1. Stel de indexeerder voor het terugstellen indexeerder in werking gebruikend veelvoudige draden.

   ```
   MAGE_INDEXER_THREADS_COUNT=10 bin/magento indexer:reindex catalog_product_price
   ```

<u> Verwachte resultaten </u>:

Er treden geen fouten op.

<u> Ware resultaten </u>:

De volgende fout wordt veroorzaakt door een verbinding AMQP: *Gebroken pijp of gesloten verbinding*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
