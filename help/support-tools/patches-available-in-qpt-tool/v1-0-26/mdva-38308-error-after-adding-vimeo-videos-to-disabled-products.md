---
title: '''MDVA-38308: Fout bij het toevoegen van Vimeo-video''s aan uitgeschakelde producten'''
description: '''De kwaliteitspatch MDVA-38308 voor Adobe Commerce lost het probleem op waarbij gebruikers het foutbericht krijgen: *Opmerking: Ongedefinieerde index: extensie in /lib/internal/Magento/Framework/File/Uploader.php op regel 806,* bij het toevoegen van Vimeo-video''s aan uitgeschakelde producten. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 is geïnstalleerd. De patch-id is MDVA-38308. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4. "'
exl-id: ed5fb9ec-c465-4bb9-8a29-4d5e4bd4c867
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# MDVA-38308: Fout bij het toevoegen van Vimeo-video&#39;s aan uitgeschakelde producten

De kwaliteitspatch MDVA-38308 voor Adobe Commerce lost het probleem op waarbij gebruikers het foutbericht krijgen: *Opmerking: Ongedefinieerde index: extensie in /lib/internal/Magento/Framework/File/Uploader.php op regel 806,* wanneer u Vimeo-video&#39;s toevoegt aan uitgeschakelde producten. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 is geïnstalleerd. De patch-id is MDVA-38308. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**
Adobe Commerce on cloud Infrastructure 2.4.1-p1, 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**
Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.5 - 2.3.6-p1, 2.4.0 - 2.4.1-p1, 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer u Vimeo-video&#39;s toevoegt aan uitgeschakelde producten, ontvangt u het volgende foutbericht:  *Opmerking: niet-gedefinieerde index: extensie in /lib/internal/Magento/Framework/File/Uploader.php op regel 806*

<u>Stappen om te reproduceren</u>:

1. Maak een eenvoudig product.
1. Schakel het gemaakte product uit.
1. Probeer een Vimeo-video toe te voegen aan het uitgeschakelde product.

<u>Verwachte resultaten</u>:

Video wordt zonder fout toegevoegd.

<u>Werkelijke resultaten</u>:

De volgende fout treedt op:
*Opmerking: niet-gedefinieerde index: extensie in /lib/internal/Magento/Framework/File/Uploader.php op regel 806*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html)

## Gerelateerde lezing

Meer informatie over het Hulpmiddel van de Patches van de Kwaliteit in onze steun kennisbasis, verwijs naar:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) in onze kennisbasis voor ondersteuning.
