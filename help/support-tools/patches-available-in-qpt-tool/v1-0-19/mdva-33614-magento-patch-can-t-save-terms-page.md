---
title: "MDVA-33614 patch: can't save Terms page"
description: 'De patch MDVA-33614 verhelpt het probleem waarbij het onmogelijk is om bewerkingen op de pagina met voorwaarden op te slaan, omdat de Page Builder de volgende fout genereert: *Er is een fout opgetreden bij het starten van de Page Builder. Neem contact op met uw contactpersoon voor technische ondersteuning*. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-33614. Dit probleem is opgelost in Adobe Commerce 2.4.2. "'
exl-id: d9b287bb-eab4-4c33-b725-ae0074962447
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-33614 patch: can&#39;t save Terms page

Het flard MDVA-33614 lost de kwestie op waar het onmogelijk is om uitgeeft aan de pagina van Termijnen te bewaren, omdat de Bouwer van de Pagina de volgende fout werpt: *een fout is voorgekomen terwijl het in werking stellen van de Bouwer van de Pagina. Raadpleeg uw contactpersoon voor technische ondersteuning* . Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 geïnstalleerd is. De patch-id is MDVA-33614. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.4.1

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce op-gebouw en Adobe Commerce op wolkeninfrastructuur 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het is niet mogelijk om bewerkingen op de pagina met voorwaarden op te slaan, omdat de Page Builder een fout genereert.

<u> Stappen om </u> te reproduceren:

1. In Commerce Admin, ga **INHOUD** > Elementen > **Pagina&#39;s**.
1. Selecteer de pagina Voorwaarden.
1. Klik **uitgeven**.
1. Maak uitgeven en klik **sparen**.

<u> Verwacht resultaat </u>:

De pagina wordt zonder fouten opgeslagen.

<u> Werkelijk resultaat </u>:

De volgende fout wordt getoond: *een fout is voorgekomen terwijl het in werking stellen van de Bouwer van de Pagina. Raadpleeg uw contactpersoon voor technische ondersteuning* .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
