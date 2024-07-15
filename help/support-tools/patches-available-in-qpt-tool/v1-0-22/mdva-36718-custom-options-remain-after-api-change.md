---
title: 'MDVA-36718: Aangepaste opties blijven na API-wijziging'
description: De patch voor het Magento MDVA-36718 verhelpt het probleem wanneer de oude aangepaste opties na het wijzigen via de API blijven bestaan.
exl-id: e9755764-e563-4921-af75-a90e06237053
feature: REST
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# MDVA-36718: Aangepaste opties blijven na API-wijziging

De patch voor het Magento MDVA-36718 verhelpt het probleem wanneer de oude aangepaste opties na het wijzigen via de API blijven bestaan.

Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 geïnstalleerd is. De patch-id is MDVA-36718. Het probleem zal volgens de planning worden opgelost in Magento versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met de versies van het Magento:**

Adobe Commerce (alle implementatiemethoden) 2.3.0-2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

1. Maak een eenvoudig product.
1. Voeg a **drop-down type** douaneoptie toe.
1. Werk de aangepaste optie via de API bij: verzend `PUT` aanvraag naar `/V1/products/options/{optionId}` .

<u> Verwachte resultaten </u>:

De aangepaste opties worden naar verwachting bijgewerkt.

<u> Ware resultaten </u>:

Er worden nieuwe aangepaste opties toegevoegd, maar de oude aangepaste opties blijven behouden.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen afhankelijk van uw implementatiemethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ het flard van de Controle voor de kwestie van het Magento met het Hulpmiddel van Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar de [ flarden beschikbaar in het hulpmiddel QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
