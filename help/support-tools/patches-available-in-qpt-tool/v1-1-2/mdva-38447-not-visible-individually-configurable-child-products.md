---
title: 'MDVA-38447: "Niet zichtbaar individueel"configureerbare kindproducten zijn teruggekeerd in de reactie van GraphQL en langzaam MySQL vraag'
description: De patch MDVA-38447 Adobe Commerce lost het probleem op waarbij "Niet zichtbaar individueel"configureerbare kindproducten in de reactie van GraphQL worden teruggegeven en vraag MySQL voor de productvraag van GraphQL met categoriefilter vertragen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 is geïnstalleerd. De patch-id is MDVA-38447. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 302e7458-d9ea-466a-a2ac-d86a8ee3eca3
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# MDVA-38447: &quot;Niet zichtbaar individueel&quot;configureerbare kindproducten zijn teruggekeerd in de reactie van GraphQL en langzaam MySQL vraag

De patch MDVA-38447 Adobe Commerce lost het probleem op waarbij &quot;Niet zichtbaar individueel&quot;configureerbare kindproducten in de reactie van GraphQL worden teruggegeven en vraag MySQL voor de productvraag van GraphQL met categoriefilter vertragen. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 geïnstalleerd is. De patch-id is MDVA-38447. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

&quot;Niet zichtbaar individueel&quot;configureerbare kindproducten zijn teruggekeerd in de reactie van GraphQL en langzaam MySQL vraag voor de productvraag van GraphQL met categoriefilter.

<u> Eerste vereisten </u>:

B2B-modules moeten worden geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Creeer een configureerbaar product met eenvoudige die producten aan **worden geplaatst individueel niet zichtbaar**.
1. Stel a **volledige herdex** in werking.
1. Stel a **vraag van GraphQL** als in werking:

<pre>query getFilteredProducts()
  $filter: ProductAttributeFilterInput!
  $sort: ProductAttributeSortInput!
  $search: String
  $pageSize: Int!
  $currentPage: Int!
) {
  products()
    filter: $filter
    sorteren: $sort
    zoekopdracht: $search
    pageSize: $pageSize
    currentPage: $currentPage
  ) {
    total_count
    page_info {
      total_pages
      current_page
      page_size
    }
    items {
      name
      sku
    }
  }
}</pre>

Variabelen:

<pre>{"filter":{"user_group":{"eq":""},"search":"config-100","sort":{},"pageSize":200,"currentPage":1}
</pre>

<u> Verwachte resultaten </u>:

Producten met zichtbaarheid ingesteld op Niet afzonderlijk zichtbaar worden niet geretourneerd als reactie op de aanvraag.

<u> Ware resultaten </u>:

Producten met zichtbaarheid ingesteld op &quot;Niet afzonderlijk zichtbaar&quot; worden als reactie gegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over kwaliteitspatches voor Adobe Commerce:

* [ vrijgegeven Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitsflarden ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
