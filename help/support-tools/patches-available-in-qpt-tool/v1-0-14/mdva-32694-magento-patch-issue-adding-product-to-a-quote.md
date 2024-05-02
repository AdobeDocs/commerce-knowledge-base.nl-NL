---
title: 'MDVA-32694 patch: issue adding product to a quote'
description: De patch MDVA-32694 lost het probleem op dat het niet mogelijk is om een geldig product in Admin toe te voegen aan een verhandelbaar citaat dat op de niet-standaard website wordt gecreeerd.
exl-id: 964abbbd-c8b1-4645-a393-7283f52e94ff
feature: Products, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-32694 patch: issue adding product to a quote

De patch MDVA-32694 lost het probleem op dat het niet mogelijk is om een geldig product in Admin toe te voegen aan een verhandelbaar citaat dat op de niet-standaard website wordt gecreeerd.

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce on cloud Infrastructure 2.3.2 met B2B versie 1.2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.3.5-p2, 2.4.0, 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Vereisten</u>:

Installeer een nieuwe Adobe Commerce-instantie met B2B.

<u>Stappen om te reproduceren</u>:

1. Ga naar **STORES > Configuratie > ALGEMEEN > B2B-functies** en **Bedrijf** en **B2B-offerte**.
1. Twee andere websites maken met **winkelen** en **verhalingen** (In totaal hebt u drie websites: *basis*, *website2*, *website3*).
1. Een eenvoudig product maken en alleen toewijzen aan *website3*.
1. Ga naar **STORES > Alle winkels** en instellen *website3* als **default**.
1. Ga naar de frontend en creeer een nieuw bedrijf op *website3*.
1. Voeg het eerder gemaakte product toe aan de winkelwagentje en maak een nieuw, verhandelbaar aanhalingsteken.
1. Ga naar **STORES > Alle winkels** en stelt u de &quot;*basis*&quot; website terug als **default**.
1. Ga naar **SALES > Aanhalingstekens > Open eerder aanhalingsteken** en probeer er hetzelfde product aan toe te voegen.

<u>Verwachte resultaten</u>:

De Admin-gebruiker kan hetzelfde product aan de offerte toevoegen, zoals verwacht.

<u>Werkelijke resultaten</u>:

De Admin-gebruiker kan niet hetzelfde product aan de prijsopgave toevoegen. Dit foutbericht wordt weergegeven:

```php
This product is assigned to another website.
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
