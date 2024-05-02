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

De patch MDVA-32012 lost het probleem op waarbij de Argentijnse en Zuid-Koreaanse postcodes niet valideren, als gevolg van wijzigingen of verschillen in de nationale postercodeformaten. De Zuid-Koreaanse postcodes moeten nu uit vijf cijfers bestaan, terwijl ze voorheen uit zes cijfers bestonden. Argentijnse postcodes kunnen zowel numeriek als alfanumeriek zijn. De patch MDVA-32012 betekent dat deze notaties voor de waarden van postcodes voor deze landen geldig zullen zijn. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.2.

## Betrokken producten en versies

* De patch is ontworpen voor Adobe Commerce op cloud-infrastructuur 2.3.5.
* De patch is ook compatibel met de volgende Adobe Commerce-versies: Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.1.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u een uit vijf cijfers bestaande Zuid-Koreaanse of alfanumerieke Argentijnse postcode invoert, verschijnt er een waarschuwing:

*De opgegeven postcode is ongeldig. Voorbeeld: [1234 (indien ingevoerd een alfanumeriek Argentijns adres)] of [123-456 (indien een uit vijf cijfers bestaand Zuid-Koreaans adres wordt ingevoerd)]. Als u vindt dat dit de juiste is, kunt u deze mededeling negeren.*

<u>Stappen om te reproduceren</u>:

1. Open de storefront.
1. Item toevoegen aan winkelwagentje.
1. Proces tot uitchecken.
1. Voeg een nieuw adres met Zuid-Korea toe voor het land en voer een uit vijf cijfers bestaande postcode in of voeg een nieuw adres met Argentinië voor het land toe en voer een alfanumerieke postcode in.
1. Probeer op te slaan.

<u>Verwachte resultaten</u>:

Het adres moet zonder waarschuwing worden opgeslagen.

<u>Werkelijke resultaten</u>:

Opslagadres retourneert een waarschuwing.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
