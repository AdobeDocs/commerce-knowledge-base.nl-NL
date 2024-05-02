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

De MDVA-40488-patch lost het probleem op waarbij configureerbare producten met kinderproducten uit de voorraad niet in hun correcte prijswaaier worden getoond. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 is geïnstalleerd. De patch-id is MDVA-40488. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De configureerbare producten met uit-van-voorraad kindproducten worden niet getoond in hun correcte prijswaaier.

<u>Vereisten</u>:

Ga naar Commerce Admin > **winkelen** > **configuratie** > **catalogus** > **Inventaris** > **aandelenopties** en instellen **Producten uit voorraad weergeven** configuratie aan *Ja*.

<u>Stappen om te reproduceren</u>:

1. Creeer een configureerbaar product met twee bijbehorende producten. Bijvoorbeeld: eenvoudige producten rood en bruin.
1. De inventaris van het eenvoudige product Rood instellen en de voorraadstatus instellen op *In voorraad* en stelt u vervolgens de status Product inschakelen in op *Nee*.
1. Stel de inventarisatie van het eenvoudige product Brown in en stel vervolgens de status Product inschakelen in op *Ja*.
1. Zorg ervoor dat de configureerbare status van de productvoorraad *In voorraad*.
1. Wijzig de inventaris van het eenvoudige product bruin in op 0 en stel de voorraadstatus in op *Uit voorraad*.
1. Op dit punt is de configureerbare status van de productvoorraad nog *In voorraad*.
1. Voer opnieuw index uit.
1. Controleer de `min_price` en `max_price` voor het configureerbare product in `catalog_product_index_price` DB-tabel - de twee waarden zijn ingesteld op 0.
1. Maar als we de configureerbare status van de productvoorraad instellen op *Uit voorraad* en herindexeren, dan kunnen we niet-nul zien `min_price` en `max_price` waarden van het configureerbare product.

<u>Verwachte resultaten</u>:

Als alle onderliggende producten *Uit voorraad* en het configureerbare product zelf is ook *Uit voorraad*, wordt de prijs berekend door alle onderliggende producten te gebruiken.

<u>Werkelijke resultaten</u>:

De `min_price` en `max_price` waarden voor het configureerbare product in `catalog_product_index_price` De lijst van DB wordt geplaatst aan 0 wanneer de configureerbare voorraadstatus is *In voorraad*, maar als het *Uit voorraad* ze worden niet-nulwaarden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
