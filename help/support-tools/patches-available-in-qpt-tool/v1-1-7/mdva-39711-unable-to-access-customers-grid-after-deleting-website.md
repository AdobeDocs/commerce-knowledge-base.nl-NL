---
title: 'MDVA-39711: Kan geen toegang krijgen tot het klantenraster nadat de website is verwijderd'
description: De MDVA-39711-patch verhelpt het probleem waarbij de Admin-gebruiker na het verwijderen van de website geen toegang heeft tot het raster van de klant. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 is geïnstalleerd. De patch-id is MDVA-39711. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: 46bef304-9360-4b69-b064-631725de381c
feature: Configuration
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-39711: Kan geen toegang krijgen tot het klantenraster nadat de website is verwijderd

De MDVA-39711-patch verhelpt het probleem waarbij de Admin-gebruiker na het verwijderen van de website geen toegang heeft tot het raster van de klant. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 is geïnstalleerd. De patch-id is MDVA-39711. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7-p2, 2.3.4-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin-gebruiker heeft na het verwijderen van de website geen toegang tot het raster van de klant.

<u>Stappen om te reproduceren</u>:

1. Maak een nieuwe website, sla deze op en sla de weergave op.
1. Maak een nieuwe klant op de beheerderswebsite en koppel deze aan de gemaakte website.
1. Ga naar **Winkels** > **Alle winkels** en verwijdert u de gemaakte website.
1. Ga naar **Klanten** > **Alle klanten**.

<u>Verwachte resultaten</u>:

* Er is geen foutbericht.
* Alle klanten zijn zichtbaar in het net.

<u>Werkelijke resultaten</u>:

* De gebruiker krijgt een foutbericht: *De website met id 2 die is aangevraagd, is niet gevonden. De website controleren en het opnieuw proberen*
* Niet alle klanten worden weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
