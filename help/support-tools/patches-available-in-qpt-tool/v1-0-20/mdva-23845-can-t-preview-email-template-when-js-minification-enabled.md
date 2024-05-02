---
title: "MDVA-23845: kan geen voorbeeld van een e-mailsjabloon bekijken als JS minification ingeschakeld is"
description: De patch voor het Magento MDVA-23845 verhelpt het probleem wanneer het niet mogelijk is een voorbeeld van de e-mailsjabloon weer te geven in Admin wanneer JS-minificatie is ingeschakeld.
exl-id: 08579251-a0aa-4e84-9d6a-3fa2999d9c05
feature: Communications, Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# MDVA-23845: kan geen voorbeeld van een e-mailsjabloon bekijken als JS minification ingeschakeld is

De patch voor het Magento MDVA-23845 verhelpt het probleem wanneer het niet mogelijk is een voorbeeld van de e-mailsjabloon weer te geven in Admin wanneer JS-minificatie is ingeschakeld.

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 is geïnstalleerd. De patch-id is MDVA-23845. Het probleem is opgelost in Magento 2.3.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor versie van Magento:** Magento Commerce Cloud 2.3.3

**Compatibel met Magento&#39;s versies:** Magento Commerce en Magneto-Commerce Cloud 2.3.2-2.3.4-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u> :

1. Inschakelen **JS-miniatuur** in **Beheer > Opslag > Configuratie > JavaScript-instellingen > JavaScript-bestanden miniaturen** = *Ja* .
1. Schakel Magento over naar productiemodus.
1. Ga naar **Beheer > Marketing > Communicatie > E-mailsjablonen** .
1. Klikken **Nieuwe sjabloon toevoegen** .
1. Selecteer de **Nieuwe volgorde** sjabloon.
1. Klik op de knop **Sjabloon laden** knop.
1. Vullen **Sjabloonnaam** with **Nieuwe volgorde.**
1. Klik op de knop **Sjabloon opslaan** knop.
1. Klik in het raster voor e-mailsjablonen op **Voorvertoning** in de **Handelingen** kolom.

<u>Verwachte resultaten</u> :

De voorvertoning van de e-mailsjabloon wordt naar behoren weergegeven in het geopende pop-upvenster.

<u>Werkelijke resultaten</u> :

De voorvertoning van de e-mailsjabloon wordt niet weergegeven in het geopende pop-upvenster. Het pop-upvenster is leeg en er kunnen JS-fouten verschijnen.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen afhankelijk van het product van uw Magento:

* Magento Commerce: Ontwikkeldocumenten [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html) .
* Magento Commerce Cloud: Ontwikkeldocumenten [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [Patch controleren op probleem met Magento met gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
