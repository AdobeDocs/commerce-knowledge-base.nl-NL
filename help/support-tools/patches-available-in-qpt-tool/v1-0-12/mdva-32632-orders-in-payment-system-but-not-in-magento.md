---
title: "MDVA-32632: Bestellingen in betalingssysteem, maar niet in Adobe Commerce"
description: De MDVA-32632 lost het probleem op waarbij orders zich in een betalingssysteem bevinden, maar niet in Adobe Commerce. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.3.5.
exl-id: f9b2fee4-9905-47cb-a71a-121426e93beb
feature: Orders, Payments, System
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# MDVA-32632: Orders in betalingssysteem, maar niet in Adobe Commerce

De MDVA-32632 lost het probleem op waarbij orders zich in een betalingssysteem bevinden, maar niet in Adobe Commerce. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.3.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.3.2-p2

**De patch is ook compatibel met Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.2 - 2.3.4-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Betaling wordt verwerkt in een betalingssysteem, maar de bestelling wordt niet in Adobe Commerce gemaakt.

<u>Stappen om te reproduceren</u>:

1. Plaats een bestelling via een online betalingsmethode.
1. Controleer de volgorde in Commerce Admin.

<u>Verwachte resultaten</u>:

Voltooide bestellingen worden nu weergegeven in het betalingssysteem en in Adobe Commerce.

<u>Werkelijke resultaten</u>:

De bestellingen zijn met succes verwerkt door het betalingssysteem, maar niet in Adobe Commerce.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
