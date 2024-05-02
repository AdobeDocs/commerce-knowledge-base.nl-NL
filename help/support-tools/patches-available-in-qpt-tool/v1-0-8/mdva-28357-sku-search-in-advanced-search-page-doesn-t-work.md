---
title: Het zoeken van SKU in Geavanceerde pagina van het Onderzoek MDVA-28357 werkt niet
description: De MDVA-28357 lost het probleem op waar onderzoek door een product SKU op de Geavanceerde pagina van het Onderzoek niet tot het relevante product leidt die in onderzoeksresultaten wordt getoond. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.4.1.
exl-id: a89409b0-3155-4fac-9842-0d129dacd6e1
feature: Search
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Het zoeken van SKU in Geavanceerde pagina van het Onderzoek MDVA-28357 werkt niet

De MDVA-28357 lost het probleem op waar onderzoek door een product SKU op de Geavanceerde pagina van het Onderzoek niet tot het relevante product leidt die in onderzoeksresultaten wordt getoond. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) versie 1.0.8 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.4.1.

## Betrokken producten en versies

* Deze patch is ontworpen voor Adobe Commerce op locatie 2.3.4-p2.
* De patch is ook compatibel met Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.0 tot 2.3.5-p2 en 2.4.0 tot 2.4.0-p1.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

In geavanceerd onderzoek, vraagt het zoeken die een SKU gebruikt het gebied van SKU gebruikend een vervanging. Een jokerteken kan echter alleen worden gebruikt met `sku.keyword`, zodat dit niet het verwachte product teruggeeft.

<u>Stappen om te reproduceren</u>

1. Ga naar Geavanceerde zoekpagina.
1. Zoeken op SKU-nummer.

<u>Werkelijk resultaat</u>

Foutbericht: *Er zijn geen objecten gevonden die aan deze zoekcriteria voldoen. Uw zoekopdracht wijzigen*.

<u>Verwacht resultaat</u>

Er wordt één product weergegeven met een bericht: *1 item is gevonden met de volgende zoekcriteria*  *SKU: XX-XXXX*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Patches toepassen met het gereedschap Kwaliteitspatches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
