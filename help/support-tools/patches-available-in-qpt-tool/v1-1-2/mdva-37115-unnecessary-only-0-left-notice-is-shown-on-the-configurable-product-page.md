---
title: '"MDVA-37115: Op de productpagina wordt de vermelding "Slechts 0 links" vermeld."'
description: De MDVA-37115-patch lost het probleem op waarbij de onnodige *Only 0 left*-kennisgeving op de configureerbare productpagina wordt weergegeven. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 is geïnstalleerd. De patch-id is MDVA-37115. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: 08aa6ac7-13ae-44c1-9db4-d449c3d8c985
feature: Configuration, Products, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# MDVA-37115: Op de productpagina wordt de vermelding &quot;Slechts 0 links&quot; vermeld

De MDVA-37115-patch lost het probleem op waarbij het onnodige *Slechts 0 links* op de configureerbare productpagina wordt een waarschuwing weergegeven. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 is geïnstalleerd. De patch-id is MDVA-37115. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle typen implementaties) 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatietypen) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een onnodige *Slechts 0 links* op de configureerbare productpagina wordt een bericht weergegeven.

<u>Vereisten</u>:

De inventarismodules worden geïnstalleerd.

<u>Stappen om te reproduceren</u>:

1. Maak een configureerbaar product met weinig opties.
1. Ga naar de voorkant.
1. Open de configureerbare productpagina en selecteer een optie.

<u>Verwachte resultaten</u>:

Nee *Slechts 0 links* op de productpagina wordt een bericht weergegeven .

<u>Werkelijke resultaten</u>:

*Slechts 0 links* op de productpagina wordt een bericht weergegeven .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
