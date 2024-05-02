---
title: 'MDVA-22383: indexeerders van doelregels traag bij index'
description: Met de MDVA-22383-patch wordt het probleem opgelost dat het opnieuw indexeren van de product/doelregel en de doelregel/productindexeerders te lang duurt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 is geïnstalleerd. De patch-id is MDVA-22383. De kwestie is opgelost in Adobe Commerce 2.3.5.
exl-id: fbf28983-5883-4769-90bd-1c97c2b2e2b8
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-22383: de indexeerders van de doelregel vertragen om te indexeren

Met de MDVA-22383-patch wordt het probleem opgelost dat het opnieuw indexeren van de product/doelregel en de doelregel/productindexeerders te lang duurt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 is geïnstalleerd. De patch-id is MDVA-22383. De kwestie is opgelost in Adobe Commerce 2.3.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce over wolkeninfrastructuur 2.3.2

**Compatibel met Adobe Commerce-versies:** Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.0-2.3.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het opnieuw indexeren van de product/doelregel en de doelregel/productindexen duurt te lang.

<u>Vereisten:</u> het probleem doet zich voor wanneer er een groot aantal producten is .

<u>Stappen om te reproduceren:</u>

1. Maak een doelregel met producten die aan de voorwaarden voldoen. De voorwaarden moeten meer product aan de verzameling toevoegen en moeten kenmerken hebben (geen categorieën of kenmerkset).
1. Voer de volgende opdracht uit:

   ```bash
       bin/magento indexer:reindex targetrule_product_rule
   ```

<u>Werkelijk resultaat:</u>

Reindexeren is vastgelopen; productbesparing blijft vastzitten.

<u>Verwacht resultaat:</u>

Het opnieuw indexeren is voltooid.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
