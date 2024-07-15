---
title: 'MDVA-30845: verbinding met verzendopdrachten mislukt'
description: De patch MDVA-30845 verhelpt het probleem waarbij *Sorry, er zijn momenteel geen aanhalingstekens beschikbaar voor deze bestelling*-fout wordt weergegeven als er tijdens het uitchecken geen verbinding wordt gemaakt met UPS XML/USPS/DHL en er geen andere verzendmethode beschikbaar is. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.2.
exl-id: 7be54213-1762-431b-bd3b-080c3d45f492
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-30845: verbinding met verzendopdrachten mislukt

Het flard MDVA-30845 bevestigt de kwestie waar *Sorry, geen citaten voor deze orde op dit ogenblik beschikbaar zijn* fout wordt getoond wanneer het er niet in slagen om met UPS XML/USPS/DHL tijdens controle te verbinden, en geen andere verschepende methode is beschikbaar. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 geïnstalleerd is. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.3.5-p2.

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce op-gebouw en Adobe Commerce op wolkeninfrastructuur 2.3.5-2.3.6.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Tijdens controle, *Sorry, zijn geen citaten beschikbaar voor deze orde op dit ogenblik* fout wordt getoond wanneer het nalaten om met UPS XML/USPS/DHL te verbinden, en geen andere verschepende methode is niet beschikbaar.

<u> Stappen om te reproduceren:</u>

1. Maak een product.
1. UPS XML Shipping method inschakelen en configureren.
1. Voeg het product toe aan de winkelwagentje.
1. Zorg ervoor dat de verzendmethoden voor UPS en vaste verzendkosten beschikbaar zijn.
1. Bewerk het hostbestand om te voorkomen dat USP verbinding maakt met de bijbehorende gateway.
1. Probeer voor de winkel de tarieven op te halen en de afhandeling opnieuw uit te voeren.

<u> Ware resultaat:</u>

*Sorry, zijn geen citaten beschikbaar voor deze orde op dit ogenblik* fout wordt getoond, en de vlakke tarief verschepen is niet beschikbaar.

<u> Verwacht resultaat:</u>

Er wordt geen foutbericht weergegeven en er is vaste verzendkosten beschikbaar.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.


## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
