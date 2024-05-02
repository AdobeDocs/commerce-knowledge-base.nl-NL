---
title: 'MDVA-37364: Aangepast kenmerk van datumtype verbreekt raster UI'
description: De patch MDVA-37364 lost het probleem op waar het attribuut van de douaneklanker van datumtype de UI van het Net van de Klant breekt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 is geïnstalleerd. De patch-id is MDVA-37364. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.4.
exl-id: d25baabf-45eb-403c-9f88-9c2448cc7b49
feature: Attributes, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37364: Aangepast kenmerk van datumtype verbreekt raster UI voor klant

De patch MDVA-37364 lost het probleem op waar het attribuut van de douaneklanker van datumtype de UI van het Net van de Klant breekt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 is geïnstalleerd. De patch-id is MDVA-37364. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0-2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Aangepast klantkenmerk van datumtype verbreekt de gebruikersinterface voor het raster van de klant.

<u>Stappen om te reproduceren</u>:

1. Een aangepast kenmerk met datumtype maken:
   * Ga naar **Winkels** > **Attributen** > **Kenmerk toevoegen**.
   * Stel het invoertype in op Datum.
   * Stel de optie Toevoegen aan kolomopties in op Ja.
   * Sla het kenmerk op.
1. Ga naar **Beheerder** > **Klanten** > **Alle klanten**.
   * Voeg het toegevoegde aangepaste kenmerk van de kolomoptie toe aan het raster.
1. Maak/bewerk een klant en stel de waarde van het gemaakte veld voor het aangepaste datumkenmerk in.
1. Cache opslaan, opnieuw indexeren en wissen.
1. Ga naar **Klanten** > **Alle klanten**.
   * Controleer het raster van de Klant.

<u>Verwachte resultaten</u>:

Het Net van de Klant Admin toont alle gegevens met inbegrip van het nieuwe attribuut van de datumdouane zonder het Net van de Klant te breken UI.

<u>Werkelijke resultaten</u>:

De interface voor het klantenraster van Admin is verbroken.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
