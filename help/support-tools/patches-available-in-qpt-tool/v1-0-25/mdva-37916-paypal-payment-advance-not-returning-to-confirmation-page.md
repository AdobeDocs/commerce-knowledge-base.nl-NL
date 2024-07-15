---
title: 'MDVA-37916: PayPal Payments Advanced not return to confirm page'
description: De kwaliteitspatch MDVA-37916 voor Adobe Commerce verhelpt het probleem met PayPal Payments Advanced dat na betaling niet terugkeert naar de bevestigingspagina. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 is geïnstalleerd. De patch-id is MDVA-37916. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 18d7bb1c-d73a-43f6-90a8-650290dfd114
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# MDVA-37916: PayPal Payments Advanced (Betalingen via PayPal) is geavanceerd en wordt niet teruggestuurd naar de bevestigingspagina

De kwaliteitspatch MDVA-37916 voor Adobe Commerce verhelpt het probleem met PayPal Payments Advanced dat na betaling niet terugkeert naar de bevestigingspagina. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 geïnstalleerd is. De patch-id is MDVA-37916. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
Adobe Commerce op cloudinfrastructuur 2.3.6-p1

**Compatibel met de versies van Adobe Commerce:**
Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.6-2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De klant wordt niet doorgestuurd naar de pagina Betalingsbevestiging na betaling met de geavanceerde PayPal-betalingsmethode.

<u> Stappen om </u> te reproduceren: [ Screencast ](https://assets.adobe.com/public/025d479b-5796-4772-6f3d-adc86306a799)

1. Voeg een product aan winkelwagentje toe en navigeer naar de betalingsstap van de betalingspagina.
1. Selecteer **Kaart van de Krediet (Geavanceerde Verhoging van de Verhoging)** betalingsoptie.
1. Klik **verdergaan** om iframe met de betalingsvorm omhoog te brengen.
1. Vul het betalingsformulier in met gegevens van de sandbox-creditcard.
   * Kaartnummer: 4444 3333 222 1111 of 4111 111 111111 111 1111
   * Vervaldatum: 12/23
   * CSC: 123
1. Klik **nu betalen**.

<u> Verwachte resultaten </u>:

Nadat de betaling is verwerkt en de betaling is gelukt, wordt u doorgestuurd naar de pagina Bestelbevestiging.

<u> Ware resultaten </u>:

* U wordt NIET omgeleid naar de pagina voor bevestiging van bestellingen.
* Maar de bestelling is gemaakt in Adobe Commerce.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) toe
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > passen Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) toe

## Gerelateerde lezing

Meer informatie over het Hulpmiddel van de Patches van de Kwaliteit in onze steun kennisbasis, verwijs naar:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar de [ flarden beschikbaar in het hulpmiddel QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie in onze steunkennisbasis.
