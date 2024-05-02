---
title: "MDVA-30862: Onjuiste besteldatum op gedrukte PDF factuur"
description: De MDVA-30862-patch verhelpt het probleem waarbij een onjuiste datum van de bestelling op de PDF-factuur wordt afgedrukt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6 is geïnstalleerd. De patch-id is MDVA-30862. Deze kwestie is opgelost in Adobe Commerce 2.4.0.
exl-id: 695f530e-6abf-4883-972d-5d9c379493a2
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# MDVA-30862: Onjuiste besteldatum op gedrukte PDF factuur

De MDVA-30862-patch verhelpt het probleem waarbij een onjuiste datum van de bestelling op de PDF-factuur wordt afgedrukt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6 is geïnstalleerd. De patch-id is MDVA-30862. Deze kwestie is opgelost in Adobe Commerce 2.4.0.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.3.4

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.4 - 2.3.7-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Onjuiste besteldatum wordt afgedrukt op de PDF factuur.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Verkoop** > **Orders**.
1. Selecteer een bestelling en druk de factuur af.

<u>Verwachte resultaten</u>:

De datum komt overeen met de aankoopdatum.

<u>Werkelijke resultaten</u>:

De datum (inclusief maand/jaar) komt niet overeen met de aankoopdatum.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
