---
title: 'ACSD-45488: configureerbaar product met meerdere bronnen die niet automatisch in voorraad worden teruggebracht'
description: De ACSD-45488-patch lost het probleem op waarbij een configureerbaar product met meerdere bronnen niet automatisch wordt teruggestuurd naar de voorraad. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 is geïnstalleerd. De patch-id is ACSD-45488. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
exl-id: 83332226-b14e-4d36-bf65-170f55fff270
feature: Configuration, Orders, Products, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# ACSD-45488: configureerbaar product met meerdere bronnen die niet automatisch in voorraad worden geretourneerd

De ACSD-45488-patch lost het probleem op waarbij een configureerbaar product met meerdere bronnen niet automatisch wordt teruggestuurd naar de voorraad. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 geïnstalleerd is. De patch-id is ACSD-45488. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een configureerbaar product met meerdere bronnen wordt niet automatisch teruggestuurd naar de voorraad.

<u> Stappen om </u> te reproduceren:

1. Een secundaire voorraadbron maken.
1. Creeer een configureerbaar product met twee bijbehorende virtuele producten.
1. Wijs de bijbehorende producten aan de standaardvoorraadbron toe en plaats de hoeveelheid aan één.
1. Controleer de `stock_status` van `cataloginventory_stock_status`.
1. Plaats zowel de bijbehorende producten om *uit voorraad* te zijn.
1. Controleer de `stock_status` van `cataloginventory_stock_status`.
1. Plaats beide bijbehorende producten om *in voorraad* te zijn.
1. Controleer de `stock_status` van `cataloginventory_stock_status`.

<u> Verwachte resultaten </u>:

De voorraadstatus van het configureerbare product wordt bijgewerkt aan *in voorraad* wanneer de bijbehorende producten worden geplaatst om in voorraad te zijn.

<u> Ware resultaten </u>:

De voorraadstatus van het configureerbare product wordt niet bijgewerkt aan *in voorraad* wanneer de bijbehorende producten worden geplaatst om in voorraad te zijn.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
