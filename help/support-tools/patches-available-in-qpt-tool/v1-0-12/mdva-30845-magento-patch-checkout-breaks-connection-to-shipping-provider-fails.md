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

De MDVA-30845-patch verhelpt het probleem waarbij de *Er zijn momenteel geen aanhalingstekens beschikbaar voor deze bestelling* Er wordt een fout weergegeven wanneer er tijdens het uitchecken geen verbinding wordt gemaakt met UPS XML/USPS/DHL en er geen andere verzendmethode beschikbaar is. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce op cloudinfrastructuur 2.3.5-p2.

**Compatibel met Adobe Commerce-versies:** Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.5-2.3.6.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Tijdens het afrekenen *Er zijn momenteel geen aanhalingstekens beschikbaar voor deze bestelling* Er wordt een fout weergegeven wanneer u geen verbinding maakt met UPS XML/USPS/DHL en er geen andere verzendmethode beschikbaar is.

<u>Stappen om te reproduceren:</u>

1. Maak een product.
1. UPS XML Shipping method inschakelen en configureren.
1. Voeg het product toe aan de winkelwagentje.
1. Zorg ervoor dat de verzendmethoden voor UPS en vaste verzendkosten beschikbaar zijn.
1. Bewerk het hostbestand om te voorkomen dat USP verbinding maakt met de bijbehorende gateway.
1. Probeer voor de winkel de tarieven op te halen en de afhandeling opnieuw uit te voeren.

<u>Werkelijk resultaat:</u>

*Er zijn momenteel geen aanhalingstekens beschikbaar voor deze bestelling* Er wordt een fout weergegeven en vaste verzendkosten zijn niet beschikbaar.

<u>Verwacht resultaat:</u>

Er wordt geen foutbericht weergegeven en er is vaste verzendkosten beschikbaar.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.


## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
