---
title: 'MDVA-36853: Geen afbeeldingen laden van grote mediagalerieën'
description: De patch MDVA-36853 verhelpt het probleem wanneer er geen afbeeldingen worden geladen omdat de widget voor het maken van een pagina-mediagalerie niet wordt geladen wanneer u een grote mediadirectory hebt.
exl-id: 64e089d9-d443-4aa7-8e04-a3598b05958d
feature: CMS, Cache, Media
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# MDVA-36853: Geen afbeeldingen laden van grote mediagalerieën

De patch MDVA-36853 verhelpt het probleem wanneer er geen afbeeldingen worden geladen omdat de widget voor het maken van een pagina-mediagalerie niet wordt geladen wanneer u een grote mediadirectory hebt.

Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 geïnstalleerd is. De patch-id is MDVA-36853. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.4.2

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce op-gebouw en Adobe Commerce op wolkeninfrastructuur 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

1. De reeks **laat Oude Galerij van Media** toe = *ja* in **Admin > Opslag > Configuratie > Geavanceerd > Systeem > de galerie van Media**.
1. Navigeer aan **Inhoud > Blokken**, en creeer een nieuw blok CMS of geef een bestaand blok CMS uit.
1. Klik op **uitgeven met de knoop van de Bouwer**.
1. Voeg een media-element toe.
1. Klik op **Uitgezocht van Galerij** knoop.

<u> Verwachte resultaten </u>:

De widget voor mediagalerie en de afbeeldingen van de mediagalerie worden beide geladen, zoals u had verwacht.

<u> Ware resultaten </u>:

De widget voor de mediagalerie en de afbeeldingen van de mediagalerie worden niet geladen wanneer u een grote map `pub/media/catalog/product/cache/` hebt.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen, afhankelijk van uw Adobe Commerce-product:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar de [ flarden beschikbaar in het hulpmiddel QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
