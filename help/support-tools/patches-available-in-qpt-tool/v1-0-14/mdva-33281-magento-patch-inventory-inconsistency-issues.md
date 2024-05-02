---
title: 'MDVA-33281 patch: Inventory inconsistency issues'
description: De MDVA-33281-patch verhelpt drie problemen op het gebied van inconsistentie bij de inventarisatie. Klik op de gekoppelde problemen in de sectie Uitgave om de stappen te bekijken waarmee deze fouten worden gereproduceerd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 is geïnstalleerd.
exl-id: adba9728-6e42-467e-943d-cf8af0bec353
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# MDVA-33281 patch: voorraadinconsistenties

De MDVA-33281-patch verhelpt drie problemen op het gebied van inconsistentie bij de inventarisatie. Klik op de gekoppelde problemen in de sectie Uitgave om de stappen te bekijken waarmee deze fouten worden gereproduceerd. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 is geïnstalleerd.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce over cloudinfrastructuur 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De patch verhelpt inconsistenties in de inventaris, zoals:

* **PHP Fatale fout** bij uitvoering `bin/magento inventory:reservation:list-inconsistencies` in CLI wegens het verkeerde de parametertype van SKU.
* **Gegevens dupliceren** in de lijst van inconsistenties.
* **Nieuwe reservering** wordt gecreëerd voordat de bestelling wordt geplaatst (vorige uitvoering op basis van reservering na geplaatste bestelling). In het geval van fouten binnen de plaatsing van de bestelling, zal extra reserve worden toegevoegd om te compenseren.

>[!NOTE]
>
>Er is ook een patch MDVA-30112 die het probleem oplost waar onverwacht een groot aantal [inconsistenties in het voorbehoud](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) in onze ontwikkelaarsdocumentatie, in `inventory_reservation` tabel. Raadpleeg voor de oplossing: [MDVA-30112 Patch voor Magento: inconsistenties bij reservering van grote aantallen](/help/support-tools/patches-available-in-qpt-tool/v1-0-8/mdva-30112-magento-patch-large-number-reservation-inconsistencies.md) in onze kennisbasis voor ondersteuning.

## Fatale PHP-fout

<u>Stappen om te reproduceren</u>:

Fatale PHP fout tijdens uitvoeren `bin/magento inventory:reservation:list-inconsistencies`.

Om een lijst van reserveringsinconsistenties te krijgen, login aan de productieserver en stel het volgende bevel in CLI in werking (-r schakelaar - ruwe output):

<pre>bin/magento-voorraad:reservation:list-inconsistenties -r</pre>

<u>Verwachte resultaten</u>:

De lijst met inconsistenties in de reserveringen wordt opgesteld. Deze worden geretourneerd in de volgende indeling

```plaintext
<ORDER_INCREMENT_ID>:<SKU>:<QUANTITY>:<STOCK-ID>
```

<u>Werkelijke resultaten</u>:

PHP Fatal Error is outputted.

## Gegevens dupliceren

Gegevens worden gedupliceerd in het dialoogvenster `inventory_reservation table`.

<u>Stappen om te reproduceren</u>:

Om reserveringsinconsistenties problemen op te lossen, stel het volgende bevel in werking:

<pre>SELECTEER *, COUNT(*) UIT GROEP Inventaris_reservering OP metagegevens, SKU, Aantal HAVING COUNT(*) &gt; 1</pre>

<u>Verwachte resultaten</u>:

Geen duplicaten.

<u>Werkelijke resultaten</u>:

Er zijn duplicaten.

## Nieuwe reservering

<u>Stappen om te reproduceren</u>:

Nieuwe reservering gemaakt vóór geplaatste order:

1. De database importeren.
1. Uitvoeren `bin/magento setup:upgrade` in de terminal.
1. Inconsistenties weergeven door uit te voeren `bin/magento inventory:reservation:list-inconsistencies        -i -r` in de terminal.

<u>Verwachte resultaten</u>:

Geen lus en veel snellere resultaten.

<u>Werkelijke resultaten</u>:

Dezelfde resultaten worden in een oneindige lus weergegeven, anders mislukt de opdracht met `memory_limit`, afhankelijk van de systeeminstellingen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
