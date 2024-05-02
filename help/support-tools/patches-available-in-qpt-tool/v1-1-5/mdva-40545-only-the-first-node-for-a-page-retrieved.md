---
title: 'MDVA-40545: Alleen het eerste knooppunt voor een pagina wordt opgehaald'
description: Met de MDVA-40545-patch wordt het probleem opgelost waarbij alleen het eerste knooppunt voor een pagina wordt opgehaald, zelfs als er meer dan één knooppunt voor dezelfde pagina is. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 is geïnstalleerd. De patch-id is MDVA-40545. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: ac7aaed9-5e81-45fe-b699-40d9c086a05c
feature: CMS, Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-40545: Alleen het eerste knooppunt voor een pagina wordt opgehaald

Met de MDVA-40545-patch wordt het probleem opgelost waarbij alleen het eerste knooppunt voor een pagina wordt opgehaald, zelfs als er meer dan één knooppunt voor dezelfde pagina is. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 is geïnstalleerd. De patch-id is MDVA-40545. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Alleen het eerste knooppunt voor een pagina wordt opgehaald, zelfs als er meerdere knooppunten voor dezelfde pagina zijn.

<u>Stappen om te reproduceren</u>:

1. Ga in het deelvenster Beheer naar **Hiërarchie** en voeg twee menupunten/knopen toe.
1. Voeg dezelfde CMS-pagina toe aan elk knooppunt.
1. Cache wissen en de voorzijde controleren.
1. Controleer de koppeling en de broodkruimels voor het eerste toegevoegde submenu.
1. Controleer de koppeling en de broodkruimels voor het tweede toegevoegde submenu.

<u>Verwachte resultaten</u>:

Broodkruimels en koppelingen in het tweede submenu zijn relevant voor het tweede knooppunt.

<u>Werkelijke resultaten</u>:

Broodkruimels en koppelingen in het tweede submenu zijn hetzelfde als het eerste submenu.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
