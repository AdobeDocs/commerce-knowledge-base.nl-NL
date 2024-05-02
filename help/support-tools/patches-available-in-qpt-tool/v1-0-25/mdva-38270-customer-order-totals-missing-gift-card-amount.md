---
title: 'MDVA-38270: Cadeaubedrag ontbreekt in totaal voor bestelling van klant'
description: De MDVA-38270-patch verhelpt het probleem wanneer het bedrag van de cadeaukaart niet wordt gevonden in het totaal voor bestellingen van klanten. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 is geïnstalleerd. De patch-id is MDVA-38270. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.
exl-id: 4ab315c4-d26e-4270-a556-66601d01fb2e
feature: Gift, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# MDVA-38270: Cadeaubedrag ontbreekt in het totaal van de bestelling van de klant

De MDVA-38270-patch verhelpt het probleem wanneer het bedrag van de cadeaukaart niet wordt gevonden in het totaal voor bestellingen van klanten. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 is geïnstalleerd. De patch-id is MDVA-38270. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**
Adobe Commerce op cloudinfrastructuur 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**
Adobe Commerce (alle implementatiemethoden) 2.4.1-2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het bedrag van de creditcard ontbreekt in de totale reactie van de bestelling.

<u>Vereisten</u>:

1. Maak een klantenaccount.
1. Plaats een bestelling met behulp van een cadeaukaart (een cadeaukaart dekt de volledige bestelling).

<u>Stappen om te reproduceren</u>:

Maak een klantenvraag voor klant, orden, punten, totaal:

```GraphQL
query {
  customer {
    orders(
      pageSize: 20
    ) {
      items {
        id
        order_date
        total {
          grand_total {
            value
            currency
          }
          total_giftcard {
              applied_balance {
                value
                currency
              }
              code
              current_balance {
                value
                currency
              }
              expiration_date
          }
        }
        status
      }
    }
  }
}
```

<u>Verwachte resultaten</u>:

`total_giftcard` is beschikbaar.

<u>Werkelijke resultaten</u>:

Er zijn geen velden beschikbaar die betrekking hebben op een cadeaukaart.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen afhankelijk van uw implementatiemethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html).

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
