---
title: 'MDVA-30186: Niet-gesorteerde kenmerkopties in GraphQL-reactie'
description: Met de MDVA-30186-patch wordt het probleem opgelost waarbij kenmerkopties niet worden gesorteerd in het GraphQL-antwoord. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 is geïnstalleerd. De patch-id is MDVA-30186. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: 7b2aef16-5012-4206-9444-e0b765f0c0c9
feature: Attributes, GraphQL, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-30186: Niet-gesorteerde kenmerkopties in GraphQL-reactie

Met de MDVA-30186-patch wordt het probleem opgelost waarbij kenmerkopties niet worden gesorteerd in het GraphQL-antwoord. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 is geïnstalleerd. De patch-id is MDVA-30186. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce over wolkeninfrastructuur 2.3.4 en 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.4 - 2.3.5-p2, 2.4.0 - 2.4.0-p1, en 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Voeg drie opties toe aan het bestaande kleurkenmerk.
1. Maak zes eenvoudige producten met opties (voorbeeld: *Optie 1*: 1 product, *Optie 2*: 2 producten, *Optie 3*: 3 producten).
1. Maak een categorie en wijs alle hierboven gemaakte producten toe.
1. Voer nu het volgende GraphQL-verzoek in met je rubriek-id:

   <pre><code class="language-graphql">
    {
      products(
        filter: { category_id: { eq: "3" } }
        pageSize: 200
        currentPage: 1
        sort: { name: ASC }
      ) {
        aggregations {
          attribute_code
          count
          label
          options {
            count
            label
            value
          }
        }
        items {
          name
          sku
          url_key
        }
      }
    }
    </code></pre>

1. Wijzig nu de sorteervolgorde van kenmerkopties op de pagina voor kenmerkbewerking in Admin.
1. Voer het bovenstaande GraphQL-verzoek opnieuw uit en bekijk de opties voor kleurkenmerken.

<u>Verwachte resultaten</u>:

De kenmerkopties worden gesorteerd op basis van de volgorde die is ingesteld in Beheer.

<u>Werkelijke resultaten</u>:

De kenmerkopties worden altijd gesorteerd op basis van het bijbehorende aantal producten.


## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
