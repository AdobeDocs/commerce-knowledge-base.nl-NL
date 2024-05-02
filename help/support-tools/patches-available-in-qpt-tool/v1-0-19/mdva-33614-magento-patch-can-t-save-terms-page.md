---
title: "MDVA-33614 patch: can't save Terms page"
description: 'De patch MDVA-33614 verhelpt het probleem waarbij het onmogelijk is om bewerkingen op de pagina met voorwaarden op te slaan, omdat de Page Builder de volgende fout genereert: *Er is een fout opgetreden bij het starten van de Page Builder. Neem contact op met uw contactpersoon voor technische ondersteuning*. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-33614. Dit probleem is opgelost in Adobe Commerce 2.4.2. "'
exl-id: d9b287bb-eab4-4c33-b725-ae0074962447
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-33614 patch: can&#39;t save Terms page

Met de MDVA-33614-patch is het probleem verholpen waarbij het onmogelijk is om bewerkingen op de pagina met voorwaarden op te slaan, omdat Page Builder de volgende fout genereert: *Er is een fout opgetreden bij het starten van de Page Builder. Neem contact op met uw contactpersoon voor technische ondersteuning*. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-33614. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met Adobe Commerce-versies:** Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het is niet mogelijk om bewerkingen op de pagina met voorwaarden op te slaan, omdat de Page Builder een fout genereert.

<u>Stappen om te reproduceren</u>:

1. Ga in Commerce Admin naar **INHOUD** > Elements > **Pagina&#39;s**.
1. Selecteer de pagina Voorwaarden.
1. Klikken **Bewerken**.
1. Bewerken en klikken **Opslaan**.

<u>Verwacht resultaat</u>:

De pagina wordt zonder fouten opgeslagen.

<u>Werkelijk resultaat</u>:

De volgende fout wordt weergegeven: *Er is een fout opgetreden bij het starten van de Page Builder. Neem contact op met uw contactpersoon voor technische ondersteuning*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
