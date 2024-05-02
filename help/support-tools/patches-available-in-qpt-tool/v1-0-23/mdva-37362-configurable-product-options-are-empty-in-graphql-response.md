---
title: 'MDVA-37362: configureerbare productopties zijn leeg in GraphQL-reactie'
description: Met de MDVA-37362-patch wordt het probleem opgelost waarbij configureerbare waarden voor productopties en variantkenmerken leeg zijn in de GraphQL-respons. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.23 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.
exl-id: a56db5e3-0841-4764-b430-d5775ebd1fe6
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# MDVA-37362: configureerbare productopties zijn leeg in GraphQL-reactie

Met de MDVA-37362-patch wordt het probleem opgelost waarbij configureerbare waarden voor productopties en variantkenmerken leeg zijn in de GraphQL-respons. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) versie 1.0.23 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

* De patch is ontworpen voor Adobe Commerce op cloud-infrastructuur 2.4.2
* De patch is ook compatibel met Adobe Commerce op locatie en Adobe Commerce op cloud-infrastructuur 2.3.4 - 2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren:</u>

1. Maak een nieuwe bron en een nieuwe voorraad die aan deze nieuwe bron is toegewezen.
1. **Winkels** > *Instellingen* > **Configuratie** > **Catalogus** > **Inventaris** > *Opties voor productvoorraad* > Stock beheren: *JA*.
1. Maak een configureerbaar product en wijs de hoeveelheid van het product toe met de nieuwe voorraad die in stap 1 is gemaakt.
1. Opnieuw indexeren.
1. Voer een GraphQL-aanvraag in.
1. Verzoek:

```java
{
  products(filter: { sku: { eq: "test-config-product" } }) {
    items {
      id
      attribute_set_id
      name
      sku
      __typename
      price_range{
        minimum_price{
          regular_price{
            value
            currency
          }
        }
      }
      categories {
        id
      }
      ... on ConfigurableProduct {
        configurable_options {
          id
          attribute_id_v2
          label
          position
          use_default
          attribute_code
          values {
            value_index
            label
          }
          product_id
        }
        variants {
          product {
            id
            name
            sku
            attribute_set_id
            ... on PhysicalProductInterface {
              weight
            }
            price_range{
              minimum_price{
                regular_price{
                  value
                  currency
                }
              }
            }
          }
          attributes {
            uid
            label
            code
            value_index
          }
        }
      }
    }
  }
}
```

<u>Verwachte resultaten:</u>

Optiewaarden en -kenmerken moeten aanwezig zijn in het antwoord.

<u>Werkelijke resultaten:</u>

```java
{
  "data": {
    "products": {
      "items": [
        {
          "id": 2048,
          "attribute_set_id": 4,
          "name": "Test Configurable Product",
          "sku": "test-config-product",
          "__typename": "ConfigurableProduct",
          "price_range": {
            "minimum_price": {
              "regular_price": {
                "value": 100,
                "currency": "USD"
              }
            }
          },
          "categories": [
            {
              "id": 3
            }
          ],
          "configurable_options": [
            {
              "id": 296,
              "attribute_id_v2": 93,
              "label": "Color",
              "position": 1,
              "use_default": false,
              "attribute_code": "color",
              "values": [],
              "product_id": 2048
            },
            {
              "id": 297,
              "attribute_id_v2": 186,
              "label": "Size",
              "position": 0,
              "use_default": false,
              "attribute_code": "size",
              "values": [],
              "product_id": 2048
            }
          ],
          "variants": [
            {
              "product": {
                "id": 2051,
                "name": "Test Configurable Product-M-Black",
                "sku": "test-config-product-M-Black",
                "attribute_set_id": 4,
                "weight": null,
                "price_range": {
                  "minimum_price": {
                    "regular_price": {
                      "value": 100,
                      "currency": "USD"
                    }
                  }
                }
              },
              "attributes": []
            },
            {
              "product": {
                "id": 2052,
                "name": "Test Configurable Product-M-Blue",
                "sku": "test-config-product-M-Blue",
                "attribute_set_id": 4,
                "weight": null,
                "price_range": {
                  "minimum_price": {
                    "regular_price": {
                      "value": 100,
                      "currency": "USD"
                    }
                  }
                }
              },
              "attributes": []
            },
            {
              "product": {
                "id": 2049,
                "name": "Test Configurable Product-S-Black",
                "sku": "test-config-product-S-Black",
                "attribute_set_id": 4,
                "weight": null,
                "price_range": {
                  "minimum_price": {
                    "regular_price": {
                      "value": 100,
                      "currency": "USD"
                    }
                  }
                }
              },
              "attributes": []
            }
          ]
        }
      ]
    }
  }
}
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
