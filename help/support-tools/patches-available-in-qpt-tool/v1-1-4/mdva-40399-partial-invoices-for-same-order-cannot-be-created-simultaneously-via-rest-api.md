---
title: "MDVA-40399: Gedeeltelijke facturen voor dezelfde bestelling kunnen niet gelijktijdig worden gemaakt via de API"
description: De patch MDVA-40399 verhelpt het probleem waarbij gedeeltelijke facturen voor dezelfde volgorde niet gelijktijdig via de Rest API kunnen worden gemaakt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 is geïnstalleerd. De patch-id is MDVA-40399. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 2444ba57-b30b-4fdf-9e5d-988cf7fa8dd1
feature: REST, Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# MDVA-40399: Gedeeltelijke facturen voor dezelfde bestelling kunnen niet gelijktijdig worden gemaakt via de API

De patch MDVA-40399 verhelpt het probleem waarbij gedeeltelijke facturen voor dezelfde volgorde niet gelijktijdig via de Rest API kunnen worden gemaakt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 is geïnstalleerd. De patch-id is MDVA-40399. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Onvolledige facturen voor dezelfde bestellingen kunnen niet gelijktijdig worden gemaakt met de Rest API.

<u>Vereisten</u>:

Een configureerbaar product met ten minste twee variaties.

<u>Stappen om te reproduceren</u>:

1. Voeg beide varianten van het configureerbare product aan de kar toe.
1. Plaats de bestelling.
1. Maak twee facturen tegelijk voor de bestelling via de rest-API.

<u>Verwachte resultaten</u>:

* Beide facturen moeten zijn gemaakt.
* `qty_invoiced` moet voor beide facturen in de `sales_order_item` tabel.
* Beide producten hadden gefactureerde hoeveelheid moeten hebben.

<u>Werkelijke resultaten</u>:

* Beide facturen zijn gemaakt.
* `qty_invoiced` wordt niet bijgewerkt op basis van een van de facturen in de `sales_order_item` tabel.
* In de beheerdersrechten **Weergave bestelling** pagina, wordt de hoeveelheid facturen slechts voor één product weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
