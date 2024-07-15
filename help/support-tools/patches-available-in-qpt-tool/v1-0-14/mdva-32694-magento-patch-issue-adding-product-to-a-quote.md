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

Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14 geïnstalleerd is. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce on cloud Infrastructure 2.3.2 met B2B versie 1.2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.3.5-p2, 2.4.0, 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Eerste vereisten </u>:

Installeer een nieuwe Adobe Commerce-instantie met B2B.

<u> Stappen om </u> te reproduceren:

1. Ga naar **STORES > Configuratie > ALGEMEEN > Eigenschappen B2B** en laat **Bedrijf** en **B2B citaat** toe.
1. Creeer 2 meer websites met **opslag** en **opslag** (In totaal zou u 3 websites moeten hebben: *basis*, *website2*, *website3*).
1. Creeer een eenvoudig product en wijs het slechts aan *website3* toe.
1. Ga naar **VOORZIENINGEN > Alle Opslag** en plaats *website3* als **gebrek**.
1. Ga naar frontend en creeer een nieuw bedrijf op *website3*.
1. Voeg het eerder gemaakte product toe aan de winkelwagentje en maak een nieuw, verhandelbaar aanhalingsteken.
1. Ga naar **VOORZIENINGEN > Alle Opslag** en plaats &quot;*basis*&quot;website terug als **gebrek**.
1. Ga naar **SALES > Citaten > Open gecreeerd vroeger citaat** en probeer om het zelfde product aan het toe te voegen.

<u> Verwachte resultaten </u>:

De Admin-gebruiker kan hetzelfde product aan de offerte toevoegen, zoals verwacht.

<u> Ware resultaten </u>:

De Admin-gebruiker kan niet hetzelfde product aan de prijsopgave toevoegen. Dit foutbericht wordt weergegeven:

```php
This product is assigned to another website.
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
