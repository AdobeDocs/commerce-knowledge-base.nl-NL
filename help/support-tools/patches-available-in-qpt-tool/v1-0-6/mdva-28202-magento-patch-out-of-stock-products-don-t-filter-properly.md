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

Het flard MDVA-28202 lost de kwestie op waar uit voorraadproducten niet behoorlijk gebruikend **Prijs** filter op een de opslagvoorkant van Adobe Commerce worden gefiltreerd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6 geïnstalleerd is.

## Betrokken producten en versies

* De patch is ontworpen voor Adobe Commerce op cloud-infrastructuur 2.3.5-p1.
* De patch is ook compatibel met Adobe Commerce op locatie en Adobe Commerce op cloud-infrastructuur 2.3.4 - 2.4.1.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De uit voorraadproducten filteren niet behoorlijk gebruikend **Prijs** filter in Commerce Admin.

<u> Vereiste:</u>

* Plaats **Vertoning uit de Producten van het Voorraad** = &quot;*ja*&quot;onder **Opslag > Configuratie > CATALOGUS > Overzicht > de Opties van het Beeld**.

<u> Stappen om te reproduceren:</u>

1. Creeer een configureerbaar product met twee eenvoudige producten (Voorbeeld: plaats **Prijs** = *$1500*).
1. Beide eenvoudige producten zouden &quot;uit voorraad&quot;moeten terwijl het creëren van het configureerbare product.
1. Wijs dit configureerbare product aan een categorie toe.
1. Indexeren en controleren van `catalog_product_index_price` tabel met entiteitskaart van het bovenstaande configureerbare product.
1. Sparen alle productprijzen = *$0*.
1. Laad de categorie en bevestig de beschikbaarheid van het product.
1. Open de **filter van de Prijs** van gelaagde navigatie.
1. Bericht dat de **filter van de Prijs** een optie van &quot; *$0.00 - $9.99* &quot; heeft.
1. Klik op dit boven **Prijs** filteroptie en plaats de **Prijs** = *$1500*, en u zult het configureerbare product krijgen wij hierboven creeerden.

<u> Verwacht resultaat:</u>

Het product filtert onder het correcte prijsbereik zoals verwacht.

<u> Ware resultaat:</u>

Het product valt onder het verkeerde prijsbereik.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen afhankelijk van uw implementatiemethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ passen flarden toe gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > passen flarden ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelingsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitsflarden ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar de [ flarden beschikbaar in het hulpmiddel QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.

Meer over configureerbare producten leren, verwijs naar dit artikel in onze ontwikkelaarsdocumentatie: [ creeer een configureerbare productleerprogramma ](https://devdocs.magento.com/guides/v2.4/rest/tutorials/configurable-product/config-product-intro.html) in onze ontwikkelaarsdocumentatie.
