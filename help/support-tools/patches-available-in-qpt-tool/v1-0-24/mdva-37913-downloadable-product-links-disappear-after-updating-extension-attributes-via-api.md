---
title: 'MDVA-37913: Koppelingen voor het downloaden van producten verdwijnen na bijwerken van extensiekenmerken via API'
description: De MDVA-37913-patch lost het probleem op waarbij de downloadbare productkoppelingen verdwijnen na het bijwerken van extensiekenmerken via de API. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 is geïnstalleerd. De patch-id is MDVA-37913. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.
exl-id: e4b2cf59-5c35-4a28-a63e-15cd7d0d5a5d
feature: REST, Attributes, Extensions, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# MDVA-37913: Koppelingen voor het downloaden van producten verdwijnen na bijwerken van extensiekenmerken via API

De MDVA-37913-patch lost het probleem op waarbij de downloadbare productkoppelingen verdwijnen na het bijwerken van extensiekenmerken via de API. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 geïnstalleerd is. De patch-id is MDVA-37913. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.


## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
Adobe Commerce over wolkeninfrastructuur 2.3.6

**Compatibel met de versies van Adobe Commerce:**
Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.0 - 2.4.0-p1
>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.


## Probleem

Downloadbare productkoppelingen verdwijnen na het bijwerken van extensiekenmerken via API.

<u> Eerste vereisten </u>:
Downloadbaar product met downloadkoppelingen.

<u> Stappen om </u> te reproduceren:

1. Werk de uitbreidingsattributen bij, gebruikend verzoek als dit:

```JSON
{
    "product": {
        "extension_attributes": {
            "stock_item": {
                "is_in_stock": true,
                "qty": 100
            }
        }
    }
}
```

<u> Verwachte resultaten </u>:<br>
Het product is bijgewerkt. Niet alle downloadkoppelingen zijn verwijderd.

<u> Ware resultaten </u>:<br>
Product bijgewerkt, maar alle downloadkoppelingen zijn verwijderd.


## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) toe
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > passen Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) toe

## Gerelateerde lezing

Meer informatie over het Hulpmiddel van de Patches van de Kwaliteit in onze steun kennisbasis, verwijs naar:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar de [ flarden beschikbaar in het hulpmiddel QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie in onze steunkennisbasis.
