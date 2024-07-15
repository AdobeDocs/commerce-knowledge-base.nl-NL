---
title: 'MDVA-32012 patch: S. Koreaans en Argentina zip codes validation'
description: De patch MDVA-32012 lost het probleem op waarbij de Argentijnse en Zuid-Koreaanse postcodes niet valideren, als gevolg van wijzigingen of verschillen in de nationale postercodeformaten. De Zuid-Koreaanse postcodes moeten nu uit vijf cijfers bestaan, terwijl ze voorheen uit zes cijfers bestonden. Argentijnse postcodes kunnen zowel numeriek als alfanumeriek zijn. De patch MDVA-32012 betekent dat deze notaties voor de waarden van postcodes voor deze landen geldig zullen zijn. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.2.
exl-id: 9602f50d-6acd-4724-9734-6aeb65393a25
feature: Communications
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# MDVA-32012 patch: S. Koreaans en Argentina zip codes validation

De patch MDVA-32012 lost het probleem op waarbij de Argentijnse en Zuid-Koreaanse postcodes niet valideren, als gevolg van wijzigingen of verschillen in de nationale postercodeformaten. De Zuid-Koreaanse postcodes moeten nu uit vijf cijfers bestaan, terwijl ze voorheen uit zes cijfers bestonden. Argentijnse postcodes kunnen zowel numeriek als alfanumeriek zijn. De patch MDVA-32012 betekent dat deze notaties voor de waarden van postcodes voor deze landen geldig zullen zijn. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 geïnstalleerd is. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.2.

## Betrokken producten en versies

* De patch is ontworpen voor Adobe Commerce op cloud-infrastructuur 2.3.5.
* De patch is ook compatibel met de volgende Adobe Commerce-versies: Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.1.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u een uit vijf cijfers bestaande Zuid-Koreaanse of alfanumerieke Argentijnse postcode invoert, verschijnt er een waarschuwing:

*verstrekte Postcode schijnt ongeldig te zijn. Voorbeeld: [ 1234 (als input een alfanumeriek adres van Argentinië) ] of [ 123-456 (als input een 5-cijferig Zuid-Koreaans adres) ]. Als u het juiste gelooft kunt u deze kennisgeving negeren.*

<u> Stappen om </u> te reproduceren:

1. Open de storefront.
1. Item toevoegen aan winkelwagentje.
1. Proces tot uitchecken.
1. Voeg een nieuw adres met Zuid-Korea toe voor het land en voer een uit vijf cijfers bestaande postcode in of voeg een nieuw adres met Argentinië voor het land toe en voer een alfanumerieke postcode in.
1. Probeer op te slaan.

<u> Verwachte resultaten </u>:

Het adres moet zonder waarschuwing worden opgeslagen.

<u> Ware resultaten </u>:

Opslagadres retourneert een waarschuwing.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
