---
title: "MDVA-34680: Klantenaccount is niet correct gefilterd op het netwerk van klanten"
description: De MDVA-34680-patch verhelpt het probleem wanneer de klantenaccount die na 00:00 UTC is gemaakt, niet correct is gefilterd op het raster van de klant. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 is geïnstalleerd. De patch-id is MDVA-34680. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.
exl-id: 2e506d7a-8cde-41eb-84b2-1a5ff8015428
feature: Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-34680: Klantenaccount is niet correct gefilterd op het raster van de klant

De MDVA-34680-patch verhelpt het probleem wanneer de klantenaccount die na 00:00 UTC is gemaakt, niet correct is gefilterd op het raster van de klant. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26 is geïnstalleerd. De patch-id is MDVA-34680. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.4.1 en 2.4.2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.6-2.3.7 en 2.4.1-2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer een klantenrekening na 00:00 UTC wordt gecreeerd, en u probeert om rekeningen tegen die datum te filtreren, zal het deze klant niet terugkeren.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Winkels** > **Configuratie** > **Algemeen** en stel de tijdzone in op Eastern Standard [Verenigde Staten/New York].
1. Maak een nieuwe klantenaccount na 00:00 UTC.
1. Ga naar **Klanten** > **Alle klanten** en filteraccounts op de datum van vandaag.

<u>Verwachte resultaten</u>:

De filters van de klantenrekening tonen de nieuwe rekening die vandaag na 00:00 UTC wordt gecreeerd.

<u>Werkelijke resultaten</u>:

De filters van de klantenrekening tonen niet de nieuwe die rekening vandaag wordt gecreeerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
