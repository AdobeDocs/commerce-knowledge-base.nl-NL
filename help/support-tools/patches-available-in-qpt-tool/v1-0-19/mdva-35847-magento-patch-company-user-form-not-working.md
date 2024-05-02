---
title: 'MDVA-35847: Bedrijfsformulier werkt niet'
description: De patch MDVA-35847 lost de kwestie van de Vorm van de Gebruiker van het Bedrijf op het werk en het terugkeren van een 500 fout op het vooreind. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-35847. Het probleem is opgelost in Adobe Commerce versie 2.4.3.
exl-id: 1a3f4a61-0c21-460a-ae48-e792d03ed805
feature: B2B, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# MDVA-35847: Formulier Bedrijfs van de Gebruiker werkt niet

De patch MDVA-35847 lost de kwestie van de Vorm van de Gebruiker van het Bedrijf op het werk en het terugkeren van een 500 fout op het vooreind. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-35847. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.4.2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.4.1-2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Vereisten</u>:

Adobe Commerce B2B is geïnstalleerd.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Winkels** > **Attributen** > **Klant** en maak een nieuw aangepast klantkenmerk:

   * Invoertype = *Datum*
   * Tonen op winkelcentrum = *Ja*
   * Sorteervolgorde = *0*
   * Forms to Use In = *Alle formulieren*

1. Maak een nieuw bedrijf.
1. Meld u aan als bedrijfsbeheerder aan de voorzijde.
1. Ga naar de secties Bedrijfs van Gebruikers.

<u>Verwachte resultaten</u>:

Het formulier Bedrijfs gebruiker wordt normaal geladen.

<u>Werkelijke resultaten</u>:

De vorm van de Gebruiker van het Bedrijf laadt en keert geen 500 fout terug.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
