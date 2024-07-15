---
title: "MDVA-40488: configureerbare producten met kinderproducten uit de buitenhandel die niet in de juiste prijsklasse worden getoond"
description: De MDVA-40488-patch lost het probleem op waarbij configureerbare producten met kinderproducten uit de voorraad niet in hun correcte prijswaaier worden getoond. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 is geïnstalleerd. De patch-id is MDVA-40488. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 0c4b9f5e-ae41-409e-b244-1d7cf948ed6f
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# MDVA-40488: configureerbare producten met kinderproducten uit de buitenvoorraad die niet in de juiste prijsklasse worden getoond

De MDVA-40488-patch lost het probleem op waarbij configureerbare producten met kinderproducten uit de voorraad niet in hun correcte prijswaaier worden getoond. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 geïnstalleerd is. De patch-id is MDVA-40488. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De configureerbare producten met uit-van-voorraad kindproducten worden niet getoond in hun correcte prijswaaier.

<u> Eerste vereisten </u>:

Ga naar Commerce Admin > **opslag** > **configuratie** > **catalogus** > **Voorraad** > **voorraadopties** en plaats **Vertoning uit de configuratie van de Producten van de Voorraad** aan *ja*.

<u> Stappen om </u> te reproduceren:

1. Creeer een configureerbaar product met twee bijbehorende producten. Bijvoorbeeld: eenvoudige producten rood en bruin.
1. Plaats inventaris van het eenvoudige product Rood, en plaats de Status van het Beeld aan *In Voorraad*, dan plaatsen de Enable status van het Product aan *Nr*.
1. Plaats inventaris van het eenvoudige product Bruin, dan plaats de Enable status van het Product aan *ja*.
1. Zorg ervoor de configureerbare status van de productvoorraad *in Voorraad* is.
1. Verander de inventaris van het eenvoudige product bruin in aan 0 en plaats de Status van de Voorraad aan *uit Voorraad*.
1. Op dit punt, is de configureerbare status van de productvoorraad nog *in Voorraad*.
1. Voer opnieuw index uit.
1. Controleer `min_price` en `max_price` voor het configureerbare product in de `catalog_product_index_price` DB-tabel - de twee waarden zijn ingesteld op 0.
1. Maar als wij de configureerbare Status van de productvoorraad aan *uit voorraad* plaatsen en herdex, dan kunnen wij niet-nul `min_price` en `max_price` waarden van het configureerbare product zien.

<u> Verwachte resultaten </u>:

Als alle kindproducten *uit Voorraad* zijn en het configureerbare product zelf ook *uit Voorraad* is, wordt de prijs berekend door alle kindproducten te gebruiken.

<u> Ware resultaten </u>:

De `min_price` en `max_price` waarden voor het configureerbare product in de `catalog_product_index_price` lijst van OB worden geplaatst aan 0 wanneer de configureerbare voorraadstatus *in voorraad* is, maar als het *uit Beeld* is worden zij niet-nul waarden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
