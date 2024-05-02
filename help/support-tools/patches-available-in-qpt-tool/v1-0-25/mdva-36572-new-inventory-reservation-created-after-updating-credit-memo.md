---
title: "MDVA-36572: Nieuwe voorraadboeking gemaakt na bijwerking van de kredietnota"
description: Met de MDVA-36572-patch is het probleem opgelost waarbij een nieuwe voorraadreservering wordt gemaakt na het bijwerken van de creditnota. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 is geïnstalleerd. De patch-id is MDVA-36572. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 6d98e1aa-0faf-4317-a6ae-386f84266b9c
feature: Inventory, Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# MDVA-36572: Nieuwe voorraadboeking gemaakt na bijwerking van de kredietnota


## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**
Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatietypen) 2.3.5-2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Update observer voor creditering van creditmemo-reservering wordt geactiveerd telkens wanneer het creditmemo wordt bijgewerkt. Volgens de overeenkomst met PO veranderde de logica van reserveringsupdate zodat deze alleen op het gecreëerde creditmemo kon worden geactiveerd. De mogelijkheid dat de creditmemo-bewerkingen via de API worden uitgevoerd, wordt door de PO eveneens in het toepassingsgebied van afzonderlijke tickets onderzocht.

<u>Stappen om te reproduceren</u>:

1. Klantenaccount maken.
1. Eenvoudig product maken.
1. Maak nieuwe bestelling, factuur en creditnota voor de bestelling.
1. Nieuwe integratie maken.
1. Tabel voorraad_reservering controleren:

   ```SQL
       select * from inventory_reservation;
       +----------------+----------+----------+----------+-------------------------------------------------------------------------------------------------------------+
       | reservation_id | stock_id | sku      | quantity | metadata                                                                                                    |
       +----------------+----------+----------+----------+-------------------------------------------------------------------------------------------------------------+
       |              1 |        1 | simple_1 |  -1.0000 | {"event_type":"order_placed","object_type":"order","object_id":"","object_increment_id":"000000001"}        |
       |              2 |        1 | simple_1 |   1.0000 | {"event_type":"creditmemo_created","object_type":"order","object_id":"1","object_increment_id":"000000001"} |
       +----------------+----------+----------+----------+-------------------------------------------------------------------------------------------------------------+
       2 rows in set (0.00 sec)
   ```

1. Aanvraag GET verzenden naar: `../rest/default/V1/creditmemo/3`
1. Reactie kopiëren (voorbeeld):

   ```JSON
       {
       "adjustment": 0,
       "adjustment_negative": 0,
       "adjustment_positive": 0,
       "base_adjustment": 0,
       "base_adjustment_negative": 0,
       "base_adjustment_positive": 0,
       "base_currency_code": "USD",
       "base_discount_amount": 0,
       "base_grand_total": 105,
       "base_discount_tax_compensation_amount": 0,
       "base_shipping_amount": 5,
       "base_shipping_incl_tax": 5,
       "base_shipping_tax_amount": 0,
       "base_subtotal": 100,
       "base_subtotal_incl_tax": 100,
       "base_tax_amount": 0,
       "base_to_global_rate": 1,
       "base_to_order_rate": 1,
       "billing_address_id": 2,
       "created_at": "2021-04-05 23:43:45",
       "discount_amount": 0,
       "entity_id": 1,
       "global_currency_code": "USD",
       "grand_total": 105,
       "discount_tax_compensation_amount": 0,
       "increment_id": "000000001",
       "order_currency_code": "USD",
       "order_id": 1,
       "shipping_address_id": 1,
       "shipping_amount": 5,
       "shipping_incl_tax": 5,
       "shipping_tax_amount": 0,
       "state": 2,
       "store_currency_code": "USD",
       "store_id": 1,
       "store_to_base_rate": 0,
       "store_to_order_rate": 0,
       "subtotal": 100,
       "subtotal_incl_tax": 100,
       "tax_amount": 0,
       "updated_at": "2021-04-05 23:43:45",
       "items": [
        {
            "base_cost": null,
            "base_discount_tax_compensation_amount": 0,
            "base_price": 100,
            "base_price_incl_tax": 100,
            "base_row_total": 100,
            "base_row_total_incl_tax": 100,
            "base_tax_amount": 0,
            "base_weee_tax_row_disposition": 0,
            "entity_id": 1,
            "discount_tax_compensation_amount": 0,
            "name": "simple_1",
            "order_item_id": 1,
            "parent_id": 1,
            "price": 100,
            "price_incl_tax": 100,
            "product_id": 1,
            "qty": 1,
            "row_total": 100,
            "row_total_incl_tax": 100,
            "sku": "simple_1",
            "tax_amount": 0,
            "weee_tax_applied": "[]",
            "weee_tax_applied_row_amount": 0,
            "weee_tax_row_disposition": 0
        }
       ],
       "comments": []
      }
   ```

1. Aanvraag POST verzenden naar: `../rest/default/V1/creditmemo`

   ```JSON
       {
       "entity":
        --paste full response from previous step here--
       }
   ```

   >[!NOTE]
   >
   >Deze lading wordt gebruikt slechts voor het vereenvoudigen van het reproduceren - de klant krijgt de zelfde kwestie na het bijwerken van hun douanekenmerk

1. Tabel voorraad_reservering controleren:

<u>Werkelijke resultaten</u>:

```sql
select * from inventory_reservation;
+----------------+----------+----------+----------+-------------------------------------------------------------------------------------------------------------+
| reservation_id | stock_id | sku      | quantity | metadata                                                                                                    |
+----------------+----------+----------+----------+-------------------------------------------------------------------------------------------------------------+
|              1 |        1 | simple_1 |  -1.0000 | {"event_type":"order_placed","object_type":"order","object_id":"","object_increment_id":"000000001"}        |
|              2 |        1 | simple_1 |   1.0000 | {"event_type":"creditmemo_created","object_type":"order","object_id":"1","object_increment_id":"000000001"} |
|              3 |        1 | simple_1 |   1.0000 | {"event_type":"creditmemo_created","object_type":"order","object_id":"1","object_increment_id":"000000001"} |
+----------------+----------+----------+----------+-------------------------------------------------------------------------------------------------------------+
3 rows in set (0.00 sec)
```

<u>Verwachte resultaten</u>:

Er wordt geen tweede reservering voor dezelfde creditmemo gemaakt.

## De patch toepassen

Om individuele flarden toe te passen gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
