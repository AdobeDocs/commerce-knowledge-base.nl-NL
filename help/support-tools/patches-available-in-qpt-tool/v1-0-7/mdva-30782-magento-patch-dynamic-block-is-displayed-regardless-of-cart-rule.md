---
title: 'MDVA-30782: dynamisch blok wordt weergegeven ongeacht de regel van het winkelwagentje.'
description: De patch MDVA-30782 verhelpt het probleem waarbij een dynamisch blok wordt weergegeven, ongeacht de regel van het winkelwagentje. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: 88da8853-aae7-4fd9-82ba-a4e9fc99cf53
feature: Cache, Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-30782: het dynamische blok wordt getoond ongeacht de kartelregel

De patch MDVA-30782 verhelpt het probleem waarbij een dynamisch blok wordt weergegeven, ongeacht de regel van het winkelwagentje. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.5 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het dynamische blok wordt weergegeven op de pagina, zelfs als niet wordt voldaan aan de voorwaarde voor de catalogusprijs.

<u>Stappen om te reproduceren</u>:

1. Maak twee producten.
1. Maak een regel voor catalogusprijzen die alleen voor een van deze producten geldt.
1. Maak een dynamisch blok en wijs de regel voor catalogusprijzen hieraan toe.
1. Maak een widget met de volgende parameters:
   * Type = dynamische blokrotatie
   * Dynamische blokken die worden weergegeven = opgegeven dynamische blokken
   * Dynamische blokken opgeven = blokformulierstap \#3Layout Updates (kan willekeurig zijn)
   * Weergeven op = Alle producttypen
   * Container = Aanvullende informatie product
1. De cache opnieuw indexeren en leegmaken.
1. Controleer beide productpagina&#39;s voor dynamische blokvorm stap \#3

<u>Verwachte resultaten</u>:

Dynamisch blok wordt alleen op de eerste productpagina weergegeven.

<u>Werkelijke resultaten</u>:

Dynamisch blok wordt op beide productpagina&#39;s weergegeven. Met Dynamische blokken aan Vertoning = de Regel van de Prijs van de Catalogus Verwant op stap \#3, is het resultaat het zelfde.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
