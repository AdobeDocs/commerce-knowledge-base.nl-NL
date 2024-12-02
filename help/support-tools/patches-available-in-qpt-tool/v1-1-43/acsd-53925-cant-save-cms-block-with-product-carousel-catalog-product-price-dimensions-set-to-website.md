---
title: 'ACSD-53925: Kan CMS-blok niet opslaan met [!UICONTROL Product Carousel]'
description: Pas de ACSD-53925-patch toe om het Adobe Commerce-probleem op te lossen waarbij de beheerder een CMS-blok niet kan opslaan met Product Carousel wanneer de dimensiemodus voor catalog_product_price op de website is ingesteld.
feature: CMS, Page Builder, Price Indexer, Products
role: Admin, Developer
exl-id: 6ef6d8ff-4ebb-4adb-9fb7-0d4a81a25f50
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-53925: Kan CMS-blok niet opslaan met *[!UICONTROL Product Carousel]*

De ACSD-53925-patch verhelpt het probleem dat de beheerder een CMS-blok niet kan opslaan met *[!UICONTROL Product Carousel]* als de dimensiemodus voor `catalog_product_price` is ingesteld op website. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.43 wordt geïnstalleerd. De patch-id is ACSD-53925. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin kan een CMS-blok met *[!UICONTROL Product Carousel]* niet opslaan wanneer de modus Dimensies voor `catalog_product_price` is ingesteld op website.

<u> Stappen om </u> te reproduceren:

1. Twee eenvoudige producten maken:
   * simple1 - $ 10
   * simple2 - $ 20
1. Creeer een bundelproduct &#39;*bundel1-dyn*&#39; met twee opties die op eenvoudige product SKUs worden gebaseerd.
1. Modus Afmetingen instellen voor de indexering van de productprijs:

   `bin/magento indexer:set-dimensions-mode catalog_product_price website`

1. Ga naar **[!UICONTROL Content]** > **[!UICONTROL Blocks]** en maak een nieuw CMS-blok.
1. Bewerk de inhoud met [!DNL Page Builder] :
   * Een element *[!UICONTROL Row]* toevoegen
   * Een element *[!UICONTROL Products]* toevoegen
   * Selecteren *[!UICONTROL Product Carousel]*
   * Ga product SKU - *bundle1-dyn* in
1. Sla het CMS-blok op.

<u> Verwachte resultaten </u>:

De gebruiker kan een productcarrousel zonder fouten toevoegen.

<u> Ware resultaten </u>:

* Een bericht wordt geworpen in UI: *wij spijt, is een fout voorgekomen terwijl het produceren van deze inhoud*
* `var/log/exception.log` bevat de volgende fout:

  ```
  [2023-08-18T20:58:14.533374+00:00] report.CRITICAL: PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'username_dev.catalog_product_index_price_ws0' doesn't exist in /test/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
  ```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
