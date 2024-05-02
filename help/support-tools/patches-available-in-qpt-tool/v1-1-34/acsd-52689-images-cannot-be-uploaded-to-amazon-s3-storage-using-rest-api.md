---
title: "ACSD-52689: images kunnen niet via REST API naar Amazon S3-opslag worden geüpload"
description: Pas de ACSD-52689-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de afbeeldingen niet via REST API naar Amazon S3-opslag kunnen worden geüpload.
feature: REST, Storage, Iaas
role: Admin
exl-id: ad072cbf-53b2-49b6-8b33-f0e23e921a1a
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-52689: afbeeldingen kunnen niet worden geüpload naar Amazon S3-opslag via REST API

De ACSD-52689-patch verhelpt het probleem waarbij de afbeeldingen niet kunnen worden geüpload naar Amazon S3-opslag met REST API Deze patch is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.34 is geïnstalleerd. De patch-id is ACSD-52689. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Afbeeldingen kunnen niet worden geüpload naar Amazon S3-opslag met REST API

<u>Stappen om te reproduceren</u>:

1. Configureer REMOTE_STORAGE voor het Amazon S3-emmertje.
1. Voeg een afbeelding aan het product toe met de Bulk-API.

   ```POST .../rest/all/async/bulk/V1/products/bySku/media```

   ```
   [
       {
           "sku": "p1",
           "entry": {
               "media_type": "image",
               "position": 0,
               "disabled": false,
               "types": [
                   "image",
                   "thumbnail",
                   "small_image",
                   "swatch_image"
               ],
               "content": {
                "type": "image\/jpeg",
                   "name": "adobe_commerce_test_3",
                   "base64_encoded_data": "/9j/4AAQSkZJRgABAQAAAQABA..."
               }
           }
       }
   ]
   ```

1. Wacht tot de bulkbewerking is verwerkt.

<u>Verwachte resultaten</u>

De afbeelding moet naar het Amazon S3-emmertje worden geüpload.

<u>Werkelijke resultaten</u>

De afbeelding wordt niet automatisch geüpload naar het Amazon S3-emmertje.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
