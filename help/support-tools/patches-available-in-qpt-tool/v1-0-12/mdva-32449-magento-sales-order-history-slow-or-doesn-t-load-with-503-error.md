---
title: "MDVA-32449: de geschiedenis van de verkooporde langzaam of laadt niet met fout 503"
description: De MDVA-32449-patch lost het probleem op in Adobe Commerce, waar de geschiedenis van de verkooporder langzaam wordt geladen of niet wordt geladen en een 503-fout wordt weergegeven. Dit is een kwestie wanneer 13000+ klanten aan een bedrijf B2B worden toegewezen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 is geïnstalleerd. Dit probleem is opgelost in Adobe Commerce 2.4.1.
exl-id: e3fd4db2-b706-4712-ba8e-270eaca7fdb2
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-32449: de geschiedenis van de verkooporde langzaam of laadt niet met fout 503

De MDVA-32449-patch lost het probleem op in Adobe Commerce, waar de geschiedenis van de verkooporder langzaam wordt geladen of niet wordt geladen en een 503-fout wordt weergegeven. Dit is een kwestie wanneer 13000+ klanten aan een bedrijf B2B worden toegewezen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 is geïnstalleerd. Dit probleem is opgelost in Adobe Commerce 2.4.1.

## Betrokken producten en versies

Dit is een kwestie wanneer 13000+ klanten aan een bedrijf B2B worden toegewezen.

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.3.5-p2, 2.4.0, 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Hiermee wordt het probleem verholpen waarbij de geschiedenis van de bestelling zeer langzaam wordt geladen of helemaal niet wordt geladen.

<u>Vereisten</u>:

13000+ klanten toegewezen aan een B2B-bedrijf

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de winkel als bedrijfsbeheerder.
1. Ga naar de pagina met historie van de verkooporder.

<u>Verwachte resultaten</u>:

De de geschiedenispagina van de verkooporde laadt normaal.

<u>Werkelijke resultaten</u>:

De pagina wordt zeer langzaam geladen of de pagina wordt mogelijk niet geladen en er wordt een time-outfout weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
