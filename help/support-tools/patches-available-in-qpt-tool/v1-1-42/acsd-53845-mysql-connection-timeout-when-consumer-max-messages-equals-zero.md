---
title: 'ACSD-53845: Time-outprobleem bij MySQL-verbinding wanneer consument max_messages = 0'
description: Pas de ACSD-53845-patch toe om het Adobe Commerce-probleem op te lossen waarbij MySQL-verbinding uitvalt wanneer de consument \ max_messages = 0`.
feature: REST, Configuration
role: Admin, Developer
exl-id: 68f862ed-5401-41e9-a6cc-cef44ebc1915
source-git-commit: 6fa7182a807147a00ad750966cd839ec18ffe0c7
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# ACSD-53845: MySQL-probleem met time-out voor verbinding bij consument `max_messages = 0`

De ACSD-53845-patch verhelpt het probleem waarbij MySQL-verbindingen uitvallen wanneer de consument `max_messages = 0`. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.42 is geïnstalleerd. De patch-id is ACSD-53845. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

MySQL-verbinding verloopt soms uit bij een consument `max_messages = 0`.

De verbinding met de database wordt echter hersteld wanneer een transactie wordt gestart.

<u>Stappen om te reproduceren</u>:

1. Een aanvraag verzenden naar bulkupdateproducten met de `async/bulk/V1/products` REST API-eindpunt.
1. Status controleren in het dialoogvenster `magento_operation` tabel.

<u>Verwachte resultaten</u>:

De producten worden bijgewerkt.

<u>Werkelijke resultaten</u>:

1. Er is een fout geregistreerd:

   ```
   report.CRITICAL: Message has been rejected: SQLSTATE[HY000]: General error: 2006 MySQL server has gone away [] []
   ```

1. *status* voor deze bewerking *4* in de `magento_operation` tabel.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
