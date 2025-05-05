---
title: 'ACSD-48417: SQL-fout na het maken van een programmawijziging'
description: Pas de ACSD-48417-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een SQL-fout optreedt nadat een wijziging in het programma voor een product is gemaakt en een ander product is opgeslagen.
exl-id: 2bbf3bb5-dec8-43b3-81f1-be0dc53d1f46
feature: Storage
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-48417: SQL-fout na het maken van een programmawijziging

De ACSD-48417-patch verhelpt het probleem waarbij een SQL-fout optreedt na het maken van een programmawijziging voor een product en het opslaan van een ander product. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 wordt geïnstalleerd. De patch-id is ACSD-48417. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er wordt een SQL-fout weergegeven na het maken van een programmawijziging voor een product en het opslaan van een ander product.

<u> Stappen om </u> te reproduceren:

1. Installeer Magento 2.4-ontwikkelt EE + de Gegevens van de Steekproef.
1. Ga naar het deelvenster Beheer > **[!UICONTROL Catalog]** > **[!UICONTROL Products]** .
1. Bewerk om het even welk product (bijvoorbeeld, Joust Duffle Bag [ SKU: 24-MB01 ]).
1. Een nieuwe update plannen:
   * Selecteren **[!UICONTROL Save as a New Update]**
   * Naam van update: &quot;Update 1&quot;
   * Begindatum: huidige tijd +1 min
   * Einddatum: huidige tijd +1 uur
   * Productnaam wijzigen in: &quot;Joust Duffle Bag 2&quot;
   * Sla het product op.
1. Ga naar CLI en voer uitsnijden uit en wacht tot het schema is toegepast.

   ```
   bin/magento cron:run && bin/magento cron:run
   ```

1. Nogmaals, ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** en geef om het even welk configureerbaar product (b.v., de Hoodie van Chaz Kangeroo [ SKU: MH01 ]) uit.

   * Alle varianten uitschakelen. Ga naar de kolom Acties > **[!UICONTROL Select]** > **[!UICONTROL Disable Product]** .
   * Sla het configureerbare bestand op.

<u> Verwachte resultaten </u>:

Geen fout bij het opslaan van het product.

<u> Ware resultaten </u>:

De volgende fout treedt op:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'sku' cannot be null, query was: INSERT INTO `catalog_product_entity` (`entity_id`, `sku`, `row_id`, `created_in`, `updated_in`) VALUES (?, ?, ?, ?, ?)
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
