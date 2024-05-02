---
title: 'MDVA-37225: Snelle volgorde werkt niet met gehele SKU'
description: De kwaliteitspatch MDVA-37225 voor Adobe Commerce verhelpt het probleem wanneer de pagina niet wordt geladen bij het maken van een snelle volgorde wanneer geïmporteerde SKU's een geheel getal bevatten. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 is geïnstalleerd. De patch-id is MDVA-37225. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.
exl-id: ecd2b9d7-ca68-4372-b0c5-55e2a3301586
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-37225: Snelle orde die niet met geheel SKU werkt

De kwaliteitspatch MDVA-37225 voor Adobe Commerce verhelpt het probleem wanneer de pagina niet wordt geladen bij het maken van een snelle volgorde wanneer geïmporteerde SKU&#39;s een geheel getal bevatten. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 is geïnstalleerd. De patch-id is MDVA-37225. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

* De patch is ontworpen voor Adobe Commerce op cloud-infrastructuur 2.4.1-p1
* De patch is ook compatibel met Adobe Commerce op locatie en Adobe Commerce op cloud-infrastructuur 2.4.1-2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Vereiste</u>:

Adobe Commerce met geïnstalleerde B2B-module

<u>Stappen om te reproduceren</u>:

1. B2B-functies voor snelle bestellingen inschakelen.
1. 4 eenvoudige producten met SKU&#39;s maken (voorbeeld-SKU&#39;s: *1000*, *001E002*, *001E02C*, en *7100824*).
1. Ga naar de ``<storefront_url>/quickorder`` pagina op de voorzijde, en probeer om een orde tot stand te brengen gebruikend een Csv- dossier met deze inhoud van het Voorbeeld:

| sku | kwik |
|---|---|
| 00100 | 1 |


<u>Verwachte resultaten</u>:

Het product (Voorbeeld: product met SKU = *1000*) aan het winkelwagentje wordt toegevoegd, zoals verwacht.

<u>Werkelijke resultaten</u>:

De pagina wordt niet geladen en er worden geen producten aan het winkelwagentje toegevoegd.


## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen in de ontwikkelaarsdocumentatie, afhankelijk van uw Adobe Commerce-product:

* Adobe Commerce en Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html)

## Gerelateerde lezing

Meer informatie over het Hulpmiddel van de Patches van de Kwaliteit in onze steun kennisbasis, verwijs naar:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) in onze kennisbasis voor ondersteuning.
