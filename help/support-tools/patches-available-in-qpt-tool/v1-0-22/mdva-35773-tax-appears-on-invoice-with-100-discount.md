---
title: 'MDVA-35773: Belasting verschijnt op factuur met 100% korting'
description: De patch MDVA-35773 verhelpt het probleem waarbij de Grand Total niet als nul wordt weergegeven op de factuur voor bestellingen met een korting van 100%. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 is geïnstalleerd. De patch-id is MDVA-35773. Het probleem is opgelost in Adobe Commerce versie 2.4.3.
exl-id: 895cb7d3-be9f-4864-9658-87ee0471f556
feature: Invoices, Marketing Tools, Orders, Personalization, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-35773: Belasting verschijnt op factuur met 100% korting

De patch MDVA-35773 verhelpt het probleem waarbij de Grand Total niet als nul wordt weergegeven op de factuur voor bestellingen met een korting van 100%. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 geïnstalleerd is. De patch-id is MDVA-35773. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over wolkeninfrastructuur 2.3.6

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.6-2.3.7 en 2.4.1-2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

1. Navigeer aan **Opslag** > **Montages** > **Configuratie** > **Verkoop** > **Belasting**.
1. Plaats **de Prijzen van de Catalogus** en **passen Korting op Prijzen** op *met inbegrip van Belasting* toe.
1. Navigeer aan **Opslag** > **de Regels van de Belasting** > **voeg Nieuwe Belastingsregel** toe.
1. Maak een belastingregel (bijvoorbeeld: alle VS met een belastingtarief van 10%) en pas deze toe.
1. Navigeer aan **de Marketing** > **Regels van de Prijs van de Kar**, en **voeg Nieuwe Regel** toe.
1. Creeer een regel met a **100% korting voor alle gebruikers**.
1. Maak een orde op Storefront:

   * Kies **Vrij Verschepend**.
   * Pas **Code van de Coupon** toe.

1. Navigeer aan **Verkoop** > **Orders**, en open uw orde.
1. Maak een factuur voor de bestelling en open deze.

<u> Verwachte resultaten </u>:

The factuur Grand Total = *$0.00*.

<u> Ware resultaten </u>:

De factuur Eindtotaal = *belastingbedrag* wordt gecreeerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
