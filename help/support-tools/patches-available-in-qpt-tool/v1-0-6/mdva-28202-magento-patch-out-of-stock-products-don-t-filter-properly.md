---
title: "MDVA-28202 patch: out of stock products don't filter correctly."
description: De MDVA-28202-patch lost het probleem op dat producten uit de voorraad niet correct worden gefilterd met het filter **Price** op een Adobe Commerce store frontend. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6 is geïnstalleerd.
exl-id: 45976602-15f3-4fef-9d90-da2b3fe6046d
feature: Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-28202 patch: out of stock products don&#39;t filter correct

De MDVA-28202-patch lost het probleem op waarbij producten uit de voorraad niet correct worden gefilterd met **Prijs** op de voorkant van een Adobe Commerce-winkel. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) versie 1.0.6 is geïnstalleerd.

## Betrokken producten en versies

* De patch is ontworpen voor Adobe Commerce op cloud-infrastructuur 2.3.5-p1.
* De patch is ook compatibel met Adobe Commerce op locatie en Adobe Commerce op cloud-infrastructuur 2.3.4 - 2.4.1.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Producten uit de voorraad filteren niet correct met **Prijs** in Commerce Admin.

<u>Vereiste:</u>

* Set **Producten uit voorraad weergeven** = &quot;*Ja*&quot; onder **Winkels > Configuratie > CATALOGUS > Inventaris > Stamopties**.

<u>Stappen om te reproduceren:</u>

1. Creeer een configureerbaar product met twee eenvoudige producten (Voorbeeld: reeks **Prijs** = *$ 1500*).
1. Beide eenvoudige producten zouden &quot;uit voorraad&quot;moeten terwijl het creëren van het configureerbare product.
1. Wijs dit configureerbare product aan een categorie toe.
1. Opnieuw indexeren en controleren `catalog_product_index_price` tabel met entiteit-id van het bovenstaande configureerbare product.
1. Bespaar alle productprijzen = *$0*.
1. Laad de categorie en bevestig de beschikbaarheid van het product.
1. Open de **Prijs** van gelaagde navigatie.
1. Let erop dat de **Prijs** filter heeft een optie &quot; *$ 0,00 - $ 9,99* &quot;.
1. Klik hierboven op dit **Prijs** filteroptie en stel de **Prijs** = *$ 1500* en u krijgt het configureerbare product dat we hierboven hebben gemaakt.

<u>Verwacht resultaat:</u>

Het product filtert onder het correcte prijsbereik zoals verwacht.

<u>Werkelijk resultaat:</u>

Het product valt onder het verkeerde prijsbereik.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen afhankelijk van uw implementatiemethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Patches toepassen met het gereedschap Kwaliteitspatches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.

Meer over configureerbare producten leren, verwijs naar dit artikel in onze ontwikkelaarsdocumentatie: [Een configureerbare zelfstudie voor het product maken](https://devdocs.magento.com/guides/v2.4/rest/tutorials/configurable-product/config-product-intro.html) in onze ontwikkelaarsdocumentatie.
