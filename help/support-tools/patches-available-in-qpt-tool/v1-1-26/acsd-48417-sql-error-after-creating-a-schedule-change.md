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

De ACSD-48417-patch verhelpt het probleem waarbij een SQL-fout optreedt na het maken van een programmawijziging voor een product en het opslaan van een ander product. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 is geïnstalleerd. De patch-id is ACSD-48417. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er wordt een SQL-fout weergegeven na het maken van een programmawijziging voor een product en het opslaan van een ander product.

<u>Stappen om te reproduceren</u>:

1. Installeer Magento 2.4-ontwikkelt EE + de Gegevens van de Steekproef.
1. Ga naar het deelvenster Beheer > **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Elk product bewerken (bijvoorbeeld Joust Duffle-tag) [SKU: 24 MB01]).
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

1. Opnieuw, ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** en bewerkt u een configureerbaar product (bijvoorbeeld Chaz Kangeroo Hoodie [SKU: MH01]).

   * Alle varianten uitschakelen. Ga naar de kolom Acties > **[!UICONTROL Select]** > **[!UICONTROL Disable Product]**.
   * Sla het configureerbare bestand op.

<u>Verwachte resultaten</u>:

Geen fout bij het opslaan van het product.

<u>Werkelijke resultaten</u>:

De volgende fout treedt op:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'sku' cannot be null, query was: INSERT INTO `catalog_product_entity` (`entity_id`, `sku`, `row_id`, `created_in`, `updated_in`) VALUES (?, ?, ?, ?, ?)
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
