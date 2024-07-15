---
title: 'MDVA-38132: Oneindige omleiding wanneer de URL voor de back-up anders is dan de standaard URL van de website'
description: De patch MDVA-38132 verhelpt het probleem van een oneindige omleiding wanneer de URL van de achterzijde afwijkt van de standaard URL van de website. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 is geïnstalleerd. De patch-id is MDVA-38132. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.
exl-id: 122145d7-0961-47f8-8ab6-a15d62996e49
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38132: Oneindige omleiding wanneer de URL voor de back-up anders is dan de standaard URL van de website

De patch MDVA-38132 verhelpt het probleem van een oneindige omleiding wanneer de URL van de achterzijde afwijkt van de standaard URL van de website. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 geïnstalleerd is. De patch-id is MDVA-38132. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
Adobe Commerce op cloudinfrastructuur 2.3.4-p2

**Compatibel met de versies van Adobe Commerce:**
Adobe Commerce (alle implementatiemethoden) 2.3.3-2.4.2-p1
>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het deelvenster Commerce Admin heeft een oneindige omleiding wanneer de URL van de achterkant anders is dan de URL van de standaardwebsite.

<u> Eerste vereisten </u>:

* Basis-URL wordt gebruikt voor zowel back-end als storefront. Base Secure URL wordt niet gebruikt.
* De webserver is zo geconfigureerd dat Adobe Commerce toegankelijk is via twee verschillende URL&#39;s. URL1 wordt gebruikt voor de installatie van Adobe Commerce.

<u> Stappen om </u> te reproduceren:

1. Ga naar Admin Comité > **Slaat** > **Configuratie** > **Web** op.
1. Oorspronkelijke basis-URL in algemene configuratie behouden. Het is je URL1.
1. Schakel over naar het bereik van de hoofdwebsite.
1. Wijzig de basis-URL in een andere URL (zie de voorwaarden voor het correct instellen van de webserver). Dit is uw URL2.
1. Cache wissen (indien nodig en mogelijk).
1. Open het deelvenster Beheer.

<u> Verwachte resultaten </u>:

Het deelvenster Beheer is geopend en kan worden genavigeerd. De opslag van de hoofdwebsite is geopend en kan worden genavigeerd.

<u> Ware resultaten </u>:

Oneindige omleiding gebeurt. Adobe Commerce leidt URL1 om naar URL2 en gaat op en neer.

## De patch toepassen

Afhankelijk van uw Adobe Commerce-product kunt u de volgende koppelingen gebruiken om afzonderlijke patches toe te passen:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar de [ flarden beschikbaar in het hulpmiddel QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
