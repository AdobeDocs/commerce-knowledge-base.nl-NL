---
title: '''MDVA-36832: afbeeldingen worden gedupliceerd op pagina''s met een weergavebreedte van 768 px'''
description: De MDVA-36832-patch verhelpt het probleem waarbij afbeeldingen worden gedupliceerd op pagina's met een weergavebreedte van 768 px. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 is geïnstalleerd. De patch-id is MDVA-36832. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 3eb0c11b-d93a-4676-afd1-8f6592c6cd6d
feature: Configuration, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-36832: afbeeldingen worden gedupliceerd op pagina&#39;s met een weergavebreedte van 768 px

De MDVA-36832-patch verhelpt het probleem waarbij afbeeldingen worden gedupliceerd op pagina&#39;s met een weergavebreedte van 768 px. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 geïnstalleerd is. De patch-id is MDVA-36832. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.3.5-p2

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce op-gebouw en Adobe Commerce op wolkeninfrastructuur 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Afbeeldingen worden gedupliceerd op pagina&#39;s met een weergavebreedte van 768 px.

<u> Stappen om te reproduceren:</u>

1. Ga naar achtergrond > INHOUD > Pagina&#39;s en bewerk een willekeurige pagina.
1. Voeg afbeeldingen toe aan de pagina.
1. Ga naar voorkant en open uitgegeven pagina.
1. Open gereedschappen voor ontwikkelaars in Chrome.
1. Schakel de apparaatweergave in en selecteer de iPad-weergave of stel de paginabreedte in op 768 px.

<u> Ware resultaat:</u>

De afbeelding wordt gedupliceerd.

<u> Verwacht resultaat:</u>

Er mag slechts één toegevoegde afbeelding zichtbaar zijn op de pagina.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
