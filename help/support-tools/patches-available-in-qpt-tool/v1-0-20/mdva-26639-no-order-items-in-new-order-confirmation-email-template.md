---
title: 'MDVA-26639: geen bestelling-items in nieuwe e-mailsjabloon voor bevestiging van bestelling'
description: De patch MDVA-26639 verhelpt het probleem bij het maken van een nieuwe bestelling. De bestellingspunten ontbreken in een bevestigings-e-mailsjabloon.
exl-id: 5d9716ab-6e57-47b0-8b38-ca98a98101e8
feature: Communications, Marketing Tools, Native Luma Frontend Development, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# MDVA-26639: geen bestelling-items in e-mailsjabloon voor bevestiging van nieuwe bestelling

De patch MDVA-26639 verhelpt het probleem bij het maken van een nieuwe bestelling. De bestellingspunten ontbreken in een bevestigings-e-mailsjabloon.

Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 geïnstalleerd is. De patch-id is MDVA-26639. De kwestie is opgelost in Adobe Commerce 2.3.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.3.3-p1

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce op-gebouw en Adobe Commerce op wolkeninfrastructuur 2.3.3-p1-2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

1. Ga naar **Opslag** > **Configuratie** > **Verkoop** > **Verkoop e-mail** > **Nieuwe Bevestiging van de Orde** en selecteer **Malplaatje: Nieuwe Bestelling van de Bestelwagen**.
1. Ga naar **Verkoop** > **Orde: Selecteer een orde**, ga dan naar **Informatie**, en selecteer **verzenden Post**.

<u> Verwachte resultaten </u>:

De bestelling-items worden zoals verwacht weergegeven in het e-mailbericht van de klant.

<u> Ware resultaten </u>:

De orderitems ontbreken in de e-mail met de bestelbon van de klant. Hetzelfde geldt als u een nieuwe sjabloon maakt en een sjabloon Nieuwe volgorde of Nieuwe volgorde (Luma) selecteert.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
