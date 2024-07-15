---
title: "MDVA-39153: Het kortingsbedrag wordt onjuist berekend tijdens de herschikking in de Admin."
description: De patch MDVA-39153 verhelpt het probleem waarbij het kortingsbedrag onjuist wordt berekend tijdens het opnieuw ordenen in de Admin. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 is geïnstalleerd. De patch-id is MDVA-39153. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: d4d11bea-a528-4eb5-8a57-8a7330975e4a
feature: Admin Workspace, Orders, Personalization, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-39153: Het kortingsbedrag wordt onjuist berekend tijdens de herschikking in de Admin

De patch MDVA-39153 verhelpt het probleem waarbij het kortingsbedrag onjuist wordt berekend tijdens het opnieuw ordenen in de Admin. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 geïnstalleerd is. De patch-id is MDVA-39153. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het bedrag van de korting wordt verkeerd berekend tijdens reorder in Admin.

<u> Stappen om </u> te reproduceren:

1. Ga naar **Admin** > **Opslag** > **Configuratie** > **Verkoop** > **Belastingen**.
1. Schakel de belasting voor de verzending in en geef deze weer in de winkelwagen.
1. Schakel de verzendmethode voor tabeltarieven in en configureer deze. ($15)
1. Maak een belastingregel voor ingebouwde belastingtarieven (voor CA).
1. Maak een regel voor de winkelprijs met een vaste korting van 5 dollar die op de hele winkelwagen en het hele verzendbedrag wordt toegepast.
1. Voeg een product met een prijs van $12 toe aan de winkelwagen en ga naar de pagina Winkelwagentje.
1. Pas de korting toe op het winkelwagentje.
1. Stel de verzendmethode in het gedeelte &quot;schattingen&quot; in op &quot;Platte snelheid&quot;.
1. Doorgaan met afrekenen tot de stappen van de revisie (plaats de bestelling niet).
1. Ga naar de startpagina en ga vervolgens terug naar de winkelwagentje.
1. Wijzig de verzendmethode in het gedeelte &quot;schattingen&quot; in &quot;Tabeltarief&quot;.

<u> Verwachte resultaten </u>:

De korting blijft gelijk - $5.

<u> Ware resultaten </u>:

De korting is $ 6,31.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
