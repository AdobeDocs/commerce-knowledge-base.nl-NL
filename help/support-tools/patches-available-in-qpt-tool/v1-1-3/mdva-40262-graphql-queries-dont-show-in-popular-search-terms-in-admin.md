---
title: "MDVA-40262: De vragen van GraphQL tonen niet in populaire onderzoekstermijnen in admin."
description: De MDVA-40262 Adobe Commerce-patch voor kwaliteit verhelpt het probleem dat GraphQL-zoekopdrachten niet worden weergegeven in populaire zoektermen in de beheerder. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.3 is geïnstalleerd. De patch-id is MDVA-40262. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 7157e47d-a042-4462-96ed-23203a3213bd
feature: Admin Workspace, GraphQL, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-40262: GraphQL query&#39;s worden niet weergegeven in populaire zoektermen in beheerders

De MDVA-40262 Adobe Commerce-patch voor kwaliteit verhelpt het probleem dat GraphQL-zoekopdrachten niet worden weergegeven in populaire zoektermen in de beheerder. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.3 is geïnstalleerd. De patch-id is MDVA-40262. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

GraphQL-query&#39;s worden niet weergegeven in populaire zoektermen in de beheerder.

<u>Vereisten</u>:

Voorbeeldgegevens moeten zijn geïnstalleerd.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Winkels** > **Configuratie** > **Catalogus** > **SEO** > **Algemene zoektermen** en instellen op inschakelen.
1. Voer de volgende GraphQL-query uit:

<pre>
<code class="language-graphql">
{
  products(
    search: "jackets"
    filter: { price: { to: "50" } }
    pageSize: 20
   ) {
    total_count
    items {
      name
      sku
    }
    page_info {
      page_size
      current_page
    }
  }
}
</code>
</pre>

<u>Verwachte resultaten</u>:

Nadat u de GraphQL-query hebt uitgevoerd om naar een product te zoeken, moet de zoekquery worden toegevoegd aan populaire zoektermen.

<u>Werkelijke resultaten</u>:

De zoekquery wordt niet toegevoegd aan populaire zoektermen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over kwaliteitspatches voor Adobe Commerce:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
