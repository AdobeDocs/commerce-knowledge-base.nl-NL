---
title: '''MDVA-31399 patch: Subtotal (incl. Belasting) in de voorwaarde van de kartelregel"'
description: De pleister MDVA-31399 voegt de *Subtotal toe (incl. Tax)* option to [cart price rule condition](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions), fixing the issue where the out of a cart price rule based on Subtotal (incl. BTW-nummer. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 is geïnstalleerd.
exl-id: ea0f4060-753a-4b0d-896b-fff54ffd1a82
feature: Marketing Tools, Orders, Shopping Cart, Taxes
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-31399 pleister: Subtotaal (incl. Belasting) in de voorwaarde van de kartelregel

Het flard MDVA-31399 voegt *Subtotal (incl. toe. Belasting)* optie aan [ de regelvoorwaarde van de kartprijs ](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions), die de kwestie bevestigen waar het onmogelijk was om een regel van de kartprijs toe te passen die op Subtotal (omvat. BTW-nummer. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 geïnstalleerd is.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.2 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het is onmogelijk om een regel van de kartprijs toe te passen die op Subtotal (incl.) wordt gebaseerd. BTW-nummer.

<u> Stappen om </u> te reproduceren:

1. Productprijs configureren om belasting op te nemen.
1. Maak een belastingregel en een belastingtarief voor 20%.
1. Creeer een product met **Prijs** = *100* (deze prijs omvat belasting).
1. Maak een nieuwe regel voor de winkelwagenprijs met de coupon &#39;10off&#39; om vaste korting van € 10 toe te passen als het subtotaal aan deze voorwaarden voldoet:

**Voorwaarden**: *als ALLE van deze voorwaarden WAAR zijn:*        * **Subtotaal** evenaart of groter dan 100.*

<u> Verwachte resultaten </u>:

Het is mogelijk een regel voor de subtotalen van de winkelprijs met coupon te maken om korting toe te passen op subtotaal inclusief belasting.

<u> Ware resultaten </u>:

Er zijn twee opties in de voorwaarden van de wortelregel: *Subtotal* en *Subtotal (Excl. Belasting)*, en wat wordt geselecteerd, wordt de regel toegepast slechts op subtotaal exclusief belasting.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
