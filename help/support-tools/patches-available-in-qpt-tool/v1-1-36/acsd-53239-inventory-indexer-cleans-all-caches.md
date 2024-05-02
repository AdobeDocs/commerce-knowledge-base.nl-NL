---
title: 'ACSD-53239: Inventory indexer wist alle caches'
description: Pas de ACSD-53239-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de inventarisindexator alle caches in de [!UICONTROL Update on Schedule] -modus.
feature: GraphQL, Inventory, Catalog Management
role: Admin, Developer
exl-id: b8e68cf7-d326-4c9e-8749-d83113de2070
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# ACSD-53239: De indexeerder van de inventaris schrapt alle geheime voorgeheugens in [!UICONTROL Update on Schedule] mode

De ACSD-53239-patch verhelpt het probleem waarbij de inventarisindexator alle caches in de [!UICONTROL Update on Schedule] -modus. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36 is geïnstalleerd. De patch-id is ACSD-53239. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.5-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De inventarisindexeerder wist alle geheime voorgeheugens in [!UICONTROL Update on Schedule] -modus.

<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Catalog Products]** en selecteer informatie *1200* producten.
2. Bijwerken *[!UICONTROL Qty]* naar een nieuwe waarde en klik op **[!UICONTROL Save]**.
3. Uitvoeren `bin/magento cron:run` onmiddellijk na het opslaan.
4. Voer de volgende GraphQL-query uit:

   ```GraphQL
   {
     storeConfig {
     absolute_footer
     }
   }
   ```

<u>Verwachte resultaten</u>

De query wordt binnen de gebruikelijke tijd verwerkt.

<u>Werkelijke resultaten</u>

De query wordt ongebruikelijk traag verwerkt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
