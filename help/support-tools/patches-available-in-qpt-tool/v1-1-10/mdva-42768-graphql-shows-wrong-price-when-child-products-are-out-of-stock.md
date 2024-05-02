---
title: "MDVA-42768: GraphQL heeft een verkeerde prijs wanneer kinderproducten uit voorraad zijn"
description: De MDVA-42768-patch verhelpt het probleem dat GraphQL de verkeerde prijs laat zien wanneer de onderliggende producten van een configureerbaar product uit voorraad zijn. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 is geïnstalleerd. De patch-id is MDVA-42768. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 012e7e21-e508-4449-98a6-4bdb41284c3a
feature: GraphQL, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# MDVA-42768: GraphQL heeft een verkeerde prijs wanneer kinderproducten uit voorraad zijn

De MDVA-42768-patch verhelpt het probleem dat GraphQL de verkeerde prijs laat zien wanneer de onderliggende producten van een configureerbaar product uit voorraad zijn. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 is geïnstalleerd. De patch-id is MDVA-42768. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als de onderliggende producten van een configureerbaar product uit voorraad zijn en de instelling Buiten-de-voorraad-producten weergeven is ingeschakeld, toont GraphQL-query de normale prijs van het product als **0**.

<u>Vereisten</u>:

Voorbeeldgegevens zijn geïnstalleerd.

<u>Stappen om te reproduceren</u>:

1. Schakel de instelling voor het weergeven van producten uit de voorraad in de Commerce-beheerder in door naar **Winkels** > **Configuratie** > **Catalogus** > **Inventaris**.
1. Creeer een configureerbaar product en wijs een eenvoudig kindproduct aan het toe.
1. De inventarisatie van het (eenvoudige) variantproduct instellen op **Uit voorraad**.
1. Opnieuw indexeren.
1. Voer de onderstaande GraphQL-query uit:

   ```GraphQL
   query {
     products(filter: { sku: { eq: "MH01" } }) {
       items {
         sku
         price_range {
           minimum_price {
             regular_price {
               value
               currency
             }
             final_price {
               value
               currency
             }
             discount {
               amount_off
               percent_off
             }
           }
           maximum_price {
             regular_price {
               value
               currency
             }
             final_price {
               value
               currency
             }
             discount {
               amount_off
               percent_off
             }
           }
         }
       }
     }
   }
   ```

1. De sectie met reacties controleren `minimum_price` > `regular price`.

<u>Verwachte resultaten</u>:

De minimale normale prijs wordt als reactie niet weergegeven als 0.

<u>Werkelijke resultaten</u>:

De minimale reguliere prijs = 0 als reactie.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
