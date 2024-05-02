---
title: 'ACSD-49973: Betere prestaties bij het ophalen van gebundelde producten via [!DNL GraphQL]'
description: Pas de ACSD-49973-patch toe om het Adobe Commerce-probleem op te lossen waarbij de prestaties afnemen bij het ophalen van gebundelde producten via [!DNL GraphQL].
exl-id: 7d7fce0f-40f9-4dec-aee7-1014690ccd7c
feature: GraphQL, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# ACSD-49973: Betere prestaties bij het ophalen van gebundelde producten via [!DNL GraphQL]

De ACSD-49973-patch verbetert de prestaties bij het ophalen van gebundelde producten via [!DNL GraphQL]. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 is geïnstalleerd. De patch-id is ACSD-49973. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prestaties nemen af wanneer gebundelde producten worden opgehaald via [!DNL GraphQL].

<u>Vereisten</u>:

Maak 2000 bundelproducten met de [Prestatiewerkset](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html).

<u>Stappen om te reproduceren</u>:

1. De optie [!DNL DB] querylogger:

   ```
   bin/magento dev:query-log:enable
   ```

1. Het volgende uitvoeren [!DNL GraphQL] query:

   ```GraphQL
   {
     products(
       search: "bundle"
       pageSize: 2000,
       sort: { relevance: DESC }
     ) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. Controleren `var/log/db.log` voor verzoeken aan de `catalog_product_bundle_selection` tabel.

<u>Verwachte resultaten</u>:

Verzoeken aan de `catalog_product_bundle_selection` de tabel mag niet voorkomen in de `var/log/db.log`.

<u>Werkelijke resultaten</u>:

Er zijn 2000 verzoeken om `catalog_product_bundle_selection` tabel die tezelfdertijd worden geactiveerd en de prestaties verminderen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
