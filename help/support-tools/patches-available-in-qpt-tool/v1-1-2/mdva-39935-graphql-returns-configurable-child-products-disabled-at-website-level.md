---
title: "MDVA-39935: GraphQL retourneert configureerbare onderliggende producten uitgeschakeld op websiteniveau"
description: De MDVA-39935 Adobe Commerce patch verhelpt het probleem waarbij GraphQL configureerbare onderliggende producten retourneert die zijn uitgeschakeld op websiteniveau. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2 is geïnstalleerd. De patch-id is MDVA-39935. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 45bd6bd9-3572-4477-a689-d6b952a3290a
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# MDVA-39935: GraphQL retourneert configureerbare onderliggende producten die op websiteniveau zijn uitgeschakeld

De MDVA-39935 Adobe Commerce patch verhelpt het probleem waarbij GraphQL configureerbare onderliggende producten retourneert die zijn uitgeschakeld op websiteniveau. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2 is geïnstalleerd. De patch-id is MDVA-39935. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

GraphQL retourneert configureerbare onderliggende producten, zelfs nadat deze op websiteniveau zijn uitgeschakeld.

<u>Stappen om te reproduceren</u>:

1. Weergave van producten uit voorraad inschakelen onder **Winkel** > **Configuratie** > **Catalogus** > **Inventaris** > **Opties voor voorraad** > **Producten uit voorraad weergeven** > **Ja**.
1. Selecteer **Configureerbaar product** met meer dan twee **Eenvoudige producten**.
1. Uitschakelen **Eenvoudig product** en sla de **Configureerbaar product**.
1. De **Configureerbaar product** gegevens met GraphQL.

<pre>
  <code class="language-graphql">
{
  products(filter: { sku: { eq: "cp1" } }) {
    items {
      __typename
      name
      sku
      ... on ConfigurableProduct {
        variants {
          product {
            __typename
            name
            sku
            color
            stock_status
          }
        }
      }
    }
  }
}
</code>
</pre>

<u>Verwachte resultaten</u>:

Uitgeschakelde producten worden NIET weergegeven in de resultaten van de variant.

<u>Werkelijke resultaten</u>:

Uitgeschakelde productgegevens worden opgehaald in de resultaten van de variant.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over kwaliteitspatches voor Adobe Commerce:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
