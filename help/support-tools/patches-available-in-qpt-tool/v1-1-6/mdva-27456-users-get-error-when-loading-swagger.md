---
title: 'MDVA-27456: Gebruikers krijgen een fout tijdens het laden van de wagen'
description: Met de MDVA-27456-patch wordt het probleem verholpen waarbij gebruikers een fout ondervinden bij het laden van de Swagger. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6 is geïnstalleerd. De patch-id is MDVA-27456. De kwestie is opgelost in Adobe Commerce 2.3.7.
exl-id: e331595f-a94b-4070-803a-60f559735b29
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# MDVA-27456: Gebruikers krijgen een fout tijdens het laden van de Swagger

Met de MDVA-27456-patch wordt het probleem verholpen waarbij gebruikers een fout ondervinden bij het laden van de Swagger. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6 is geïnstalleerd. De patch-id is MDVA-27456. De kwestie is opgelost in Adobe Commerce 2.3.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.3.5-p1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.5 - 2.3.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers krijgen een fout tijdens het laden van de wagen.

<u>Stappen om te reproduceren</u>:

Ga naar `../swagger.`

<u>Verwachte resultaten</u>:

De wagen wordt zonder fout geladen.

<u>Werkelijke resultaten</u>:

Gebruikers krijgen de volgende fout: *Kan API-definitie niet laden*. Foutlogboek bevat:

*report.CRITICAL: Report ID: webapi-5ea9c6da19cb1; Bericht: Het parametertype &quot;\DateTime&quot; is ongeldig. Controleer de parameter en probeer het opnieuw.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
