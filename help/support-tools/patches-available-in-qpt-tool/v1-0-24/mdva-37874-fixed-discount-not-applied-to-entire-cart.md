---
title: "MDVA-37874: Vaste korting niet toegepast op hele winkelwagen"
description: De MDVA-37874-patch verhelpt het probleem wanneer de **vaste korting** voor het hele winkelwagentje onjuist wordt toegepast op een bundelproduct dat meer dan één optie bevat. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.24 is geïnstalleerd. De patch-id is MDVA-37874. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.
exl-id: a1c414f0-b654-4b18-b502-47351513ddfa
feature: Orders, Personalization, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# MDVA-37874: Vaste korting niet toegepast op hele winkelwagen

De MDVA-37874-patch verhelpt het probleem wanneer de **vast kortingsbedrag** voor het hele winkelwagentje wordt ten onrechte toegepast op een bundelproduct dat meer dan één optie bevat. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.24 is geïnstalleerd. De patch-id is MDVA-37874. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

* De patch is ontworpen voor Adobe Commerce op cloud-infrastructuur 2.4.2
* De patch is ook compatibel met Adobe Commerce op locatie en Adobe Commerce op cloud-infrastructuur 2.3.6-2.3.7 en 2.4.1-2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem


<u>Stappen om te reproduceren</u>:

1. Een winkelwagentregel maken met een **vast kortingsbedrag** voor de hele kar.
1. Voeg een bundelproduct toe aan het winkelwagentje (het bundelproduct moet verschillende geselecteerde opties bevatten.)
1. Ga naar de winkelwagentje pagina en controleer de korting.


<u>Verwachte resultaten</u>:

De vaste korting wordt toegepast op het hele winkelwagentje, zoals verwacht.

<u>Werkelijke resultaten</u>:

De vaste korting wordt slechts op een deel van de winkelwagen toegepast.


## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen, afhankelijk van uw Adobe Commerce-product:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
