---
title: 'MDVA-40101: Objecten blijven een miniwinkelwagentje na bestelling PayPal Express Checkout'
description: De MDVA-40101-patch verhelpt het probleem dat items niet uit de mini-kar worden verwijderd nadat een bestelling met PayPal Express Checkout is geplaatst. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 is geïnstalleerd. De patch-id is MDVA-40101. Deze kwestie is opgelost in Adobe Commerce 2.4.0.
exl-id: d640dfcd-6fb6-4cc6-8817-3ae19aa59bed
feature: Checkout, Orders, Payments, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-40101: Objecten blijven miniwinkelwagentje na bestelling PayPal Express Checkout

De MDVA-40101-patch verhelpt het probleem dat items niet uit de mini-kar worden verwijderd nadat een bestelling met PayPal Express Checkout is geplaatst. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 is geïnstalleerd. De patch-id is MDVA-40101. Deze kwestie is opgelost in Adobe Commerce 2.4.0.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.3.7

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.2 - 2.3.7-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De objecten blijven in de mini-kar staan, zelfs nadat een bestelling met PayPal Express Checkout is geplaatst.

<u>Stappen om te reproduceren</u>:

Plaats een bestelling met PayPal Express Checkout in de modus Incognito in een browser.

<u>Verwachte resultaten</u>:

Mini-cart moet leeg zijn nadat de bestelling met succes is voltooid.

<u>Werkelijke resultaten</u>:

* Op de succespagina ziet u een lege miniwinkelwagen.
* Alle andere pagina&#39;s tonen een miniwinkelwagentje met aangeschafte objecten.
* Als u op de koppeling Kar klikt, wordt u omgeleid naar een lege kartpagina.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
