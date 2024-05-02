---
title: "MDVA-40961: Er kan geen extra item aan het winkelwagentje worden toegevoegd als de minimumhoeveelheid artikel al in het winkelwagentje staat."
description: De MDVA-40961-patch verhelpt het probleem dat een extra item niet aan het winkelwagentje kan worden toegevoegd als de minimumhoeveelheid van het item al in het winkelwagentje staat. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 is geïnstalleerd. De patch-id is MDVA-40961. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: fc90c2b6-f631-49ff-81b0-e41918dd79a7
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-40961: Er kan geen extra item aan het winkelwagentje worden toegevoegd als de minimumhoeveelheid item al in het winkelwagentje staat

De MDVA-40961-patch verhelpt het probleem dat een extra item niet aan het winkelwagentje kan worden toegevoegd als de minimumhoeveelheid van het item al in het winkelwagentje staat. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 is geïnstalleerd. De patch-id is MDVA-40961. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een extra item kan niet aan het winkelwagentje worden toegevoegd als de minimumhoeveelheid van het artikel al in het winkelwagentje staat.

<u>Stappen om te reproduceren</u>:

1. Een eenvoudig product instellen voor meer dan één **Minimale toegestane hoeveelheid in winkelwagentje** (bijvoorbeeld twee).
1. Open het product op de Storefront en voeg er twee toe aan het winkelwagentje.
1. Blijf op de productpagina en voeg nog een product aan de winkelwagentje toe.

<u>Verwachte resultaten</u>:

Het derde product kan aan het karretje worden toegevoegd omdat het al de minimumhoeveelheid bevat.

<u>Werkelijke resultaten</u>:

U krijgt het volgende foutbericht: *Het minste wat u kunt kopen, is 2*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
