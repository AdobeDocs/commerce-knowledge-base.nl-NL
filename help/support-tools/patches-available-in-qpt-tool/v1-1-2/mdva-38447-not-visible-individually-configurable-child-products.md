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

De patch MDVA-38447 Adobe Commerce lost het probleem op waarbij &quot;Niet zichtbaar individueel&quot;configureerbare kindproducten in de reactie van GraphQL worden teruggegeven en vraag MySQL voor de productvraag van GraphQL met categoriefilter vertragen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 is geïnstalleerd. De patch-id is MDVA-38447. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

&quot;Niet zichtbaar individueel&quot;configureerbare kindproducten zijn teruggekeerd in de reactie van GraphQL en langzaam MySQL vraag voor de productvraag van GraphQL met categoriefilter.

<u>Vereisten</u>:

B2B-modules moeten worden geïnstalleerd.

<u>Stappen om te reproduceren</u>:

1. Een configureerbaar product maken met eenvoudige producten die zijn ingesteld op **Niet afzonderlijk zichtbaar**.
1. Een **volledige redex**.
1. Een **GraphQL-query** als:

<pre>query getFilteredProducts( $filter: ProductAttributeFilterInput!
  $sort: ProductAttributeSortInput!
  $search: String $pageSize: Int!
  $currentPage: Int!
) { products( filter: $filter sort: $sort search: $search pageSize: $pageSize currentPage: $currentPage ) { total_count page_info { total_pages current_page_size } items { name sku } }</pre>

Variabelen:

<pre>{"filter":{"user_group":{"eq":""},"search":"config-100","sort":{},"pageSize":200,"currentPage":1}
</pre>

<u>Verwachte resultaten</u>:

Producten met zichtbaarheid ingesteld op Niet afzonderlijk zichtbaar worden niet geretourneerd als reactie op de aanvraag.

<u>Werkelijke resultaten</u>:

Producten met zichtbaarheid ingesteld op &quot;Niet afzonderlijk zichtbaar&quot; worden als reactie gegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over kwaliteitspatches voor Adobe Commerce:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
