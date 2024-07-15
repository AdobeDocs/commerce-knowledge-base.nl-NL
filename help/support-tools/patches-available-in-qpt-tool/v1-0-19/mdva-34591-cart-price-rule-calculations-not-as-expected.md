---
title: "MDVA-34591: Berekening van de prijsregel voor winkelwagentjes niet zoals verwacht"
description: De MDVA-34591-patch verhelpt het probleem dat de kartprijsregel met **Maximale korting op de hoeveelheid wordt toegepast op *** niet correct werkt als meerdere regels voor de kartprijs worden toegepast. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-34591. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.
exl-id: 1fa196bb-aab1-4364-a1b0-7c31d6d27d6d
feature: Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# MDVA-34591: Berekening van de prijsegel voor winkelwagentjes niet zoals verwacht

Het flard MDVA-34591 bevestigt de kwestie waar de regel van de kartprijs met **Maximale Korting van de Kant op** wordt toegepast niet correct werkt als de veelvoudige regels van de kartprijs worden toegepast. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 geïnstalleerd is. De patch-id is MDVA-34591. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over wolkeninfrastructuur 2.3.6

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.0-2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

1. Ga naar Admin, en creeer de volgende twee regels:

   * Regel 1: $10 van maximaal drie objecten in de winkelwagentje. Plaats prioriteit = *3*.
   * Regel 2: 50% van alle producten in de kar. Plaats prioriteit = *1*.

1. Ga naar de winkel.

1. Voeg acht hoeveelheden van een product toe dat aan prijs = *$51* elk aan de kar wordt geplaatst.

1. Controleer de korting in de winkelwagentje.

<u> Verwachte resultaten </u>:

De correcte berekende korting is $234, zoals verwacht.

* Berekeningen:

  Gelijke regels voor de kartonprijs: artikel 2, regel 1\
  Regel 2 toepassen (50% korting), dus Korting = $204\
  Regel 1 toepassen (10 van 3 objecten), dus Korting = $30\
  Totale korting = MIN ( 408/2 + 10x3, 8 &#42; 51) = MIN (204 + 30, 8 &#42; 51) = $234

<u> Ware resultaten </u>:

De korting wordt onjuist berekend op $153, veroorzaakt door de verkeerde hoeveelheid die wordt gebruikt voor de berekening van de maximale kortingswaarde, aangezien de vaste korting wordt toegepast ongeacht het bedrag van de producten in het winkelwagentje.

* Berekeningen:

  Gelijke regels voor de kartonprijs: artikel 2, regel 1\
  Regel 2 toepassen (50% korting), dus Korting = $204\
  Regel 1 toepassen (10 van 3 objecten), dus Korting = $30\
  Totale korting = MIN (204 + 30, 3 &#42; 51) = $153

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
