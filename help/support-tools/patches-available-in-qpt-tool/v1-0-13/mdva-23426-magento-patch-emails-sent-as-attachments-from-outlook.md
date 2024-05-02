---
title: 'MDVA-23426 Magento patch: email sent as attachments from Outlook'
description: De patch voor MDVA-23426-Magento's verhelpt het probleem waarbij e-mails als bijlagen worden verzonden door Magento van MS Outlook. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 is geïnstalleerd. De kwestie is in Magento 2.3.5 opgelost.
exl-id: 0b4c3e33-76c5-48b0-b1a8-a967cea11b98
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# patch voor MDVA-23426-Magento: e-mails verzonden als bijlagen vanuit Outlook

De patch voor MDVA-23426-Magento&#39;s verhelpt het probleem waarbij e-mails als bijlagen worden verzonden door Magento van MS Outlook. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 is geïnstalleerd. De kwestie is in Magento 2.3.5 opgelost.

## Betrokken producten en versies

**De patch wordt gemaakt voor versie van Magento:** Magento Commerce Cloud 2.3.3.

**Compatibel met Magento&#39;s versies:** Magento Commerce en Magento Commerce Cloud 2.3.3 - 2.3.4-p2.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

E-mails worden ontvangen met een leeg gedeelte en de inhoud wordt opgenomen als bijlage.

<u>Vereisten:</u> De vooruitzichten/de Uitwisseling worden gebruikt als cliënt/servercombinatie.

<u>Stappen om te reproduceren:</u> 1. Een bestelling verzenden. De opdrachtmelding of de kennisgeving van verzending wordt verzonden.2. Het e-mailbericht is ontvangen.

<u>Werkelijk resultaat:</u> Het e-mailbericht wordt weergegeven met een leeg gedeelte en de inhoud wordt opgenomen als een bijlage met het label ATT\* bij het e-mailbericht. <u>Verwacht resultaat:</u>

Het e-mailbericht wordt zonder bijlage ontvangen en de inhoud van het e-mailbericht staat in de tekst.

## De patch toepassen

Voor instructies over hoe te om een flard QPT toe te passen, gebruik de volgende verbindingen afhankelijk van uw product van het Magento:

* Magento Commerce: Ontwikkeldocumenten [Patches toepassen met het gereedschap Kwaliteitspatches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) .
* Magento Commerce Cloud: Ontwikkeldocumenten [Upgrades and Patches > Apply patches](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [Patch controleren op probleem met Magento met gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
