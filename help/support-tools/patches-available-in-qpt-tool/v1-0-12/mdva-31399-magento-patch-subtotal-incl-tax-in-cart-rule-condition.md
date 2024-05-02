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

De MDVA-31399-patch voegt de *Subtotaal Belasting)* optie voor [voorwaarde van de kartonprijs](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions), waarin de kwestie werd geregeld waar het onmogelijk was een op subtotaal gebaseerde regel voor de kartprijs toe te passen (incl. BTW-nummer. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 is geïnstalleerd.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.2 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het is onmogelijk om een regel van de kartprijs toe te passen die op Subtotal (incl.) wordt gebaseerd. BTW-nummer.

<u>Stappen om te reproduceren</u>:

1. Productprijs configureren om belasting op te nemen.
1. Maak een belastingregel en een belastingtarief voor 20%.
1. Een product maken met **Prijs** = *100* (deze prijs omvat ook belastingen).
1. Maak een nieuwe regel voor de winkelwagenprijs met de coupon &#39;10off&#39; om vaste korting van € 10 toe te passen als het subtotaal aan deze voorwaarden voldoet:

**Voorwaarden**: *Als ALLE van deze voorwaarden WAAR zijn:*        * **Subtotaal** gelijk aan of groter dan 100.*

<u>Verwachte resultaten</u>:

Het is mogelijk een regel voor de subtotalen van de winkelprijs met coupon te maken om korting toe te passen op subtotaal inclusief belasting.

<u>Werkelijke resultaten</u>:

Er zijn twee opties in de voorwaarden van de kartelregel: *Subtotaal* en *Subtotaal (m.u.v. Belasting)* en wat er ook wordt geselecteerd, de regel wordt alleen toegepast op subtotaal exclusief belasting.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
