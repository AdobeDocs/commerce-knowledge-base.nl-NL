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

Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 geïnstalleerd is. De patch-id is MDVA-23845. Het probleem is opgelost in Magento 2.3.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor Magento versie:** Magento Commerce Cloud 2.3.3

**Compatibel met Magento versies:** Magento Commerce en Commerce Cloud 2.3.2-2.3.4-p2 Magneto

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

1. Laat **minificatie JS** in **toe Admin > Sporen > Configuratie > de Montages van JavaScript > de Dossiers van JavaScript** = *ja*.
1. Schakel Magento over naar productiemodus.
1. Ga naar **Admin > de Marketing > Mededelingen > E-mailMalplaatjes**.
1. Klik **toevoegen Nieuw Malplaatje**.
1. Selecteer het **Nieuwe malplaatje van de Orde**.
1. Klik **Malplaatje van de Lading** knoop.
1. Vul {de Naam van 0} Malplaatje **met** Nieuwe Orde.****
1. Klik **sparen Malplaatje** knoop.
1. In het e-mailmalplaatjeraster, klik op **verbinding van de Voorproef** in de **3} kolom van Acties.**

<u> Verwachte resultaten </u>:

De voorvertoning van de e-mailsjabloon wordt naar behoren weergegeven in het geopende pop-upvenster.

<u> Ware resultaten </u>:

De voorvertoning van de e-mailsjabloon wordt niet weergegeven in het geopende pop-upvenster. Het pop-upvenster is leeg en er kunnen JS-fouten verschijnen.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen afhankelijk van het product van uw Magento:

* Magento Commerce: DevDocs [ Gids van de Update van de Software > past Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html) toe.
* Magento Commerce Cloud: DevDocs [ Verbeteringen en Patches > passen Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitsflarden ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) zelf-te dienen.
* [ het flard van de Controle voor de kwestie van het Magento met het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar de [ flarden beschikbaar in het hulpmiddel QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
