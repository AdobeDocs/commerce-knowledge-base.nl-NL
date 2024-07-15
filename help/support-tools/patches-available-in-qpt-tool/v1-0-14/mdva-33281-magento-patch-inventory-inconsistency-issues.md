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

De MDVA-33281-patch verhelpt drie problemen op het gebied van inconsistentie bij de inventarisatie. Klik op de gekoppelde problemen in de sectie Uitgave om de stappen te bekijken waarmee deze fouten worden gereproduceerd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 geïnstalleerd is.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce over cloudinfrastructuur 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De patch verhelpt inconsistenties in de inventaris, zoals:

* **PHP Onherstelbare fout** wanneer het lopen `bin/magento inventory:reservation:list-inconsistencies` in CLI wegens het verkeerde de parametertype van SKU.
* **dupliceer gegevens** in inconsistenties lijst.
* **Nieuwe reserve** zal vóór geplaatste orde worden gecreeerd (vorige realisatie die op reserve na geplaatste orde wordt gebaseerd). In het geval van fouten binnen de plaatsing van de bestelling, zal extra reserve worden toegevoegd om te compenseren.

>[!NOTE]
>
>Er is ook een flard MDVA-30112 die de kwestie oplost waar er een onverwacht groot aantal [ inconsistenties van de reservering ](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) in onze ontwikkelaarsdocumentatie, in de `inventory_reservation` lijst is. Voor de oplossing, verwijs naar [ MDVA-30112 flard van het Magento: de inconsistenties van de grote aantalreserve ](/help/support-tools/patches-available-in-qpt-tool/v1-0-8/mdva-30112-magento-patch-large-number-reservation-inconsistencies.md) in onze steunkennisbasis.

## Fatale PHP-fout

<u> Stappen om </u> te reproduceren:

PHP Fatale error when running `bin/magento inventory:reservation:list-inconsistencies`.

Om een lijst van reserveringsinconsistenties te krijgen, login aan de productieserver en stel het volgende bevel in CLI in werking (-r schakelaar - ruwe output):

<pre>bin/magento inventariseren :reservation: lijst-inconsistenties - r</pre>

<u> Verwachte resultaten </u>:

De lijst met inconsistenties in de reserveringen wordt opgesteld. Deze worden geretourneerd in de volgende indeling

```plaintext
<ORDER_INCREMENT_ID>:<SKU>:<QUANTITY>:<STOCK-ID>
```

<u> Ware resultaten </u>:

PHP Fatal Error is outputted.

## Gegevens dupliceren

Dubbele gegevens bevinden zich in de `inventory_reservation table` .

<u> Stappen om </u> te reproduceren:

Om reserveringsinconsistenties problemen op te lossen, stel het volgende bevel in werking:

<pre>SELECTEREN *, COUNT(*)
FROM voorraad_reserve
GROEP OP metagegevens, SKU, hoeveelheid
AANTAL (*) &gt; 1</pre>

<u> Verwachte resultaten </u>:

Geen duplicaten.

<u> Ware resultaten </u>:

Er zijn duplicaten.

## Nieuwe reservering

<u> Stappen om </u> te reproduceren:

Nieuwe reservering gemaakt vóór geplaatste order:

1. De database importeren.
1. Voer `bin/magento setup:upgrade` uit in de terminal.
1. Maak een lijst van inconsistenties door `bin/magento inventory:reservation:list-inconsistencies        -i -r` in de terminal uit te voeren.

<u> Verwachte resultaten </u>:

Geen lus en veel snellere resultaten.

<u> Ware resultaten </u>:

Dezelfde resultaten worden in een oneindige lus weergegeven, anders mislukt de opdracht bij `memory_limit` , afhankelijk van de systeeminstellingen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
