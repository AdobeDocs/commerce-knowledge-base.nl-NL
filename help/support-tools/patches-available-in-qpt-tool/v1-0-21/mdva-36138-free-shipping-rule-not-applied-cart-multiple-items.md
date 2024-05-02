---
title: 'MDVA-36138: regel voor gratis verzending is niet van toepassing op meerdere winkels.'
description: De MDVA-36138-patch verhelpt het probleem dat wanneer er meerdere objecten in de winkelwagen voorkomen, de overeenkomende SKU in de Free Shipping er geen gratis verzending op toepast. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 is geïnstalleerd. De patch-id is MDVA-36138. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: 74e25ca8-e4fa-47f4-ab95-561f70e05727
feature: Orders, Shipping/Delivery, Personalization, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-36138: regel voor gratis verzending is niet van toepassing op meerdere winkels

De MDVA-36138-patch verhelpt het probleem dat wanneer er meerdere objecten in de winkelwagen voorkomen, de overeenkomende SKU in de Free Shipping er geen gratis verzending op toepast. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 is geïnstalleerd. De patch-id is MDVA-36138. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.3.4

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.2 en hoger

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als een regel voor gratis verzending alleen op specifieke objecten wordt toegepast, is de korting niet van toepassing als er andere objecten in de winkelwagentje staan.

<u>Stappen om te reproduceren</u>:

1. Eenvoudige producten maken: simple1 en simple2.
1. Configureer USPS (of elke andere methode voor online verzending):

   * Toegestane methoden: Priority Mail (één methode die is geselecteerd om geen lange lijst met methoden in winkelwagentje en kassa te hebben).
   * Gratis methode: prioritaire e-mail.

1. Een winkelwagentregel maken:

   * couponcode opgeven
   * Voorwaarden, tabblad: leeg laten
   * Tabblad Handelingen:

   `Condition: SKU is simple1`
   `Free Shipping: For matching items only`

1. Voeg simple1 toe aan het winkelwagentje.
1. Pas de couponcode toe.
1. Voeg simple2 toe aan de winkelwagen.

<u>Verwachte resultaten</u>:

* simple1 - heeft gratis verzending nodig.
* simple2 - de verzendkosten moeten worden betaald.

<u>Werkelijke resultaten</u>:

De verzendprijs omvat simple1 en simple2.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
