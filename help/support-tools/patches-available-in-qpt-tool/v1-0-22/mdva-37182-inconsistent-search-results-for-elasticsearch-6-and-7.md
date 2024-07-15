---
title: "MDVA-37182: inconsistente zoekresultaten in Elasticsearch 6 en 7"
description: De patch MDVA-37182 verhelpt het probleem met inconsequent zoekgedrag in verschillende versies 6 en 7 van de Elasticsearch. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 is geïnstalleerd. De patch-id is MDVA-37182. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.
exl-id: 6c4e2d2f-cced-487d-b253-fd0c80bc6067
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-37182: inconsistente zoekresultaten in Elasticsearch 6 en 7

De patch MDVA-37182 verhelpt het probleem met inconsequent zoekgedrag in verschillende versies 6 en 7 van de Elasticsearch. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 geïnstalleerd is. De patch-id is MDVA-37182. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.4.1

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce op-gebouw en Adobe Commerce op wolkeninfrastructuur 2.4.1-2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Inconsistent zoekgedrag.

<u> Stappen om </u> te reproduceren:

1. Maak producten met de volgende details:
   * Namen: &quot;5127AC&quot;, &quot;5127SS&quot;, &quot;5127AB&quot;
   * SKU&#39;s: &quot;product1&quot;, &quot;product2&quot;, &quot;product3&quot;
1. Stel de zoekmachine in op Elasticsearch 6 (ES6).
1. Voer de volledige redex uit.
1. Zoek in de winkel naar &quot;5127s&quot;.
1. Stel de zoekmachine in op Elasticsearch 7 (ES7).
1. Voer de volledige redex uit.
1. Zoek in de winkel naar &quot;5127s&quot;.

<u> Ware resultaat:</u>:

ES6: zoekopdracht geeft geen resultaten.ES7: zoekopdracht retourneert drie producten.

<u> Verwacht resultaat:</u>:

Met Zoeken wordt één product voor beide versies geretourneerd.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen, afhankelijk van uw Adobe Commerce-product:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar de [ flarden beschikbaar in het hulpmiddel QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
