---
title: 'MDVA-40262: GraphQL query''s worden niet weergegeven in populaire zoektermen in beheerders'
description: De MDVA-40262 Adobe Commerce-patch voor kwaliteit verhelpt het probleem dat GraphQL-zoekopdrachten niet worden weergegeven in populaire zoektermen in de beheerder. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.3 is geïnstalleerd. De patch-id is MDVA-40262. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 7157e47d-a042-4462-96ed-23203a3213bd
feature: Admin Workspace, GraphQL, Search
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-40262: GraphQL query&#39;s worden niet weergegeven in populaire zoektermen in beheerders

De MDVA-40262 Adobe Commerce-patch voor kwaliteit verhelpt het probleem dat GraphQL-zoekopdrachten niet worden weergegeven in populaire zoektermen in de beheerder. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.3 geïnstalleerd is. De patch-id is MDVA-40262. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

GraphQL-query&#39;s worden niet weergegeven in populaire zoektermen in de beheerder.

<u> Eerste vereisten </u>:

Voorbeeldgegevens moeten zijn geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Ga naar **Opslag** > **Configuratie** > **Catalogus** > **SEO** > **Populaire Termen van het Onderzoek** en reeks om toe te laten.
1. Voer de volgende GraphQL-query uit:

<pre>
<code class="language-graphql">
&lbrace;
  products(
    search: "jackets"
    filter: { price: { to: "50" } }
    pageSize: 20
   ) &lbrace;
    total_count
    items &lbrace;
      name
      sku
    &rbrace;
    page_info &lbrace;
      page_size
      current_page
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u> Verwachte resultaten </u>:

Nadat u de GraphQL-query hebt uitgevoerd om naar een product te zoeken, moet de zoekquery worden toegevoegd aan populaire zoektermen.

<u> Ware resultaten </u>:

De zoekquery wordt niet toegevoegd aan populaire zoektermen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over kwaliteitspatches voor Adobe Commerce:

* [ vrijgegeven Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitsflarden ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
