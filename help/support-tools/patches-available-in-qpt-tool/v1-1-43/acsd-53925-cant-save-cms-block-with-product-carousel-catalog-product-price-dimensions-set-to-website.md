---
title: 'ACSD-53925: Kan CMS-blok niet opslaan met [!UICONTROL Product Carousel]'
description: Pas de ACSD-53925-patch toe om het Adobe Commerce-probleem op te lossen waarbij de beheerder een CMS-blok niet kan opslaan met Product Carousel wanneer de dimensiemodus voor 'catalog_product_price' is ingesteld op de website.
feature: CMS, Page Builder, Price Indexer, Products
role: Admin, Developer
exl-id: 6ef6d8ff-4ebb-4adb-9fb7-0d4a81a25f50
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-53925: Kan CMS-blok niet opslaan met *[!UICONTROL Product Carousel]*

De ACSD-53925-patch verhelpt het probleem waarbij de beheerder een CMS-blok niet kan opslaan met *[!UICONTROL Product Carousel]* wanneer de afmetingsmodus voor `catalog_product_price` is ingesteld op website. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.43 is geïnstalleerd. De patch-id is ACSD-53925. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin kan een CMS-blok niet opslaan met *[!UICONTROL Product Carousel]* wanneer de afmetingsmodus voor `catalog_product_price` is ingesteld op website.

<u>Stappen om te reproduceren</u>:

1. Twee eenvoudige producten maken:
   * simple1 - $ 10
   * simple2 - $ 20
1. Een bundelproduct maken &#39;*bundle1-dyn*&#39; met twee opties op basis van eenvoudige product-SKU&#39;s.
1. Modus Afmetingen instellen voor de indexering van de productprijs:

   `bin/magento indexer:set-dimensions-mode catalog_product_price website`

1. Ga naar **[!UICONTROL Content]** > **[!UICONTROL Blocks]** en maak een nieuw CMS-blok.
1. De inhoud bewerken met [!DNL Page Builder]:
   * Voeg een *[!UICONTROL Row]* element
   * Voeg een *[!UICONTROL Products]* element
   * Selecteren *[!UICONTROL Product Carousel]*
   * Product-SKU invoeren - *bundle1-dyn*
1. Sla het CMS-blok op.

<u>Verwachte resultaten</u>:

De gebruiker kan een productcarrousel zonder fouten toevoegen.

<u>Werkelijke resultaten</u>:

* Een bericht wordt geworpen in UI: *Er is helaas een fout opgetreden bij het genereren van deze inhoud*
* `var/log/exception.log` bevat de volgende fout:

  ```
  [2023-08-18T20:58:14.533374+00:00] report.CRITICAL: PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'username_dev.catalog_product_index_price_ws0' doesn't exist in /test/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
  ```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
