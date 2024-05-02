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

De patch MDVA-37182 verhelpt het probleem met inconsequent zoekgedrag in verschillende versies 6 en 7 van de Elasticsearch. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.2 is geïnstalleerd. De patch-id is MDVA-37182. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met Adobe Commerce-versies:** Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.4.1-2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Inconsistent zoekgedrag.

<u>Stappen om te reproduceren</u>:

1. Maak producten met de volgende details:
   * Namen: &quot;5127AC&quot;, &quot;5127SS&quot;, &quot;5127AB&quot;
   * SKU&#39;s: &quot;product1&quot;, &quot;product2&quot;, &quot;product3&quot;
1. Stel de zoekmachine in op Elasticsearch 6 (ES6).
1. Voer de volledige redex uit.
1. Zoek in de winkel naar &quot;5127s&quot;.
1. Stel de zoekmachine in op Elasticsearch 7 (ES7).
1. Voer de volledige redex uit.
1. Zoek in de winkel naar &quot;5127s&quot;.

<u>Werkelijk resultaat:</u>:

ES6: zoekopdracht geeft geen resultaten.ES7: zoekopdracht retourneert drie producten.

<u>Verwacht resultaat:</u>:

Met Zoeken wordt één product voor beide versies geretourneerd.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen, afhankelijk van uw Adobe Commerce-product:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
