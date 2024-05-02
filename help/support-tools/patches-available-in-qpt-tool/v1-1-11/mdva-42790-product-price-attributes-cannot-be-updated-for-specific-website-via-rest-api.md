---
title: 'MDVA-42790: Productprijskenmerken kunnen niet worden bijgewerkt voor specifieke websites via REST API'
description: De MDVA-42790-patch verhelpt het probleem dat gebruikers de productprijskenmerken van specifieke websites niet via REST API kunnen bijwerken. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 is geïnstalleerd. De patch-id is MDVA-42790. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: b9d80190-17d2-436f-86d5-33689b8224d4
feature: REST, Attributes, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-42790: Productprijskenmerken kunnen niet worden bijgewerkt voor specifieke websites via REST API

De MDVA-42790-patch verhelpt het probleem dat gebruikers de productprijskenmerken van specifieke websites niet via REST API kunnen bijwerken. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 is geïnstalleerd. De patch-id is MDVA-42790. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers kunnen de productprijskenmerken van specifieke websites niet bijwerken via REST API.

<u>Stappen om te reproduceren</u>:

1. Ga in Admin naar **Winkels** > **Configuratie** > **Catalogus** > **Prijs** > en set **Bereik catalogusprijs** naar website.
1. Speciale prijs voor een gebundeld product bijwerken met REST API, `POST rest/V1/products/`.

   ```JSON
   {
     "product": {
       "id": 46,
       "sku": "24-WG080",
       "name": "Sprite Yoga Companion Kit",
       "attribute_set_id": 4,
       "price": 10,
       "status": 1,
       "visibility": 1,
       "type_id": "bundle",
       "weight": 0,
       "custom_attributes": [
         {
           "attribute_code": "special_price",
           "value": "2"
         }
       ]
     }
   }
   ```

<u>Verwachte resultaten</u>:

De speciale prijs wordt bijgewerkt voor het gebundelde product wanneer **Bereik catalogusprijs** is ingesteld op Website.

<u>Werkelijke resultaten</u>:

De speciale prijs wordt niet bijgewerkt voor het gebundelde product wanneer **Bereik catalogusprijs** is ingesteld op Website.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
