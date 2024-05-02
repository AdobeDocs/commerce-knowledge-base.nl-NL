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

De ACSD-45488-patch lost het probleem op waarbij een configureerbaar product met meerdere bronnen niet automatisch wordt teruggestuurd naar de voorraad. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 is geïnstalleerd. De patch-id is ACSD-45488. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een configureerbaar product met meerdere bronnen wordt niet automatisch teruggestuurd naar de voorraad.

<u>Stappen om te reproduceren</u>:

1. Een secundaire voorraadbron maken.
1. Creeer een configureerbaar product met twee bijbehorende virtuele producten.
1. Wijs de bijbehorende producten aan de standaardvoorraadbron toe en plaats de hoeveelheid aan één.
1. Controleer de `stock_status` van `cataloginventory_stock_status`.
1. Beide bijbehorende producten instellen op *uit voorraad*.
1. Controleer de `stock_status` van `cataloginventory_stock_status`.
1. Beide bijbehorende producten instellen op *in voorraad*.
1. Controleer de `stock_status` van `cataloginventory_stock_status`.

<u>Verwachte resultaten</u>:

De voorraadstatus van het configureerbare product wordt bijgewerkt aan *in voorraad* wanneer de betrokken producten in voorraad zijn.

<u>Werkelijke resultaten</u>:

De voorraadstatus van het configureerbare product wordt niet bijgewerkt aan *in voorraad* wanneer de betrokken producten in voorraad zijn.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
