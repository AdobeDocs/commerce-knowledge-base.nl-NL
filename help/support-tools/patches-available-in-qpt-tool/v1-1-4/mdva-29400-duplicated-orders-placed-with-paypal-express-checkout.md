---
title: 'MDVA-29400: dubbele bestellingen geplaatst met PayPal Express Checkout'
description: De MDVA-29400-patch lost het probleem op waarbij dubbele bestellingen worden gemaakt wanneer klanten bestellingen plaatsen met PayPal Express Checkout. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 is geïnstalleerd. De patch-id is MDVA-29400. De kwestie is opgelost in Adobe Commerce 2.4.1.
exl-id: 75b943c8-5f7c-4d94-ae92-935428fdfcf8
feature: Checkout, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-29400: dubbele bestellingen geplaatst met PayPal Express Checkout

De MDVA-29400-patch lost het probleem op waarbij dubbele bestellingen worden gemaakt wanneer klanten bestellingen plaatsen met PayPal Express Checkout. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 is geïnstalleerd. De patch-id is MDVA-29400. De kwestie is opgelost in Adobe Commerce 2.4.1.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.3.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er worden dubbele bestellingen gemaakt wanneer gebruikers bestellingen plaatsen met PayPal Express Checkout.

<u>Vereisten</u>:

Ingeschakeld en geconfigureerd PayPal Express Checkout.

<u>Stappen om te reproduceren</u>:

1. Voeg een product toe aan winkelwagentje.
1. Ga naar de betalingspagina en gebruik PayPal Express als betalingsmethode.
1. De pagina wordt omgeleid naar paypal/express/review/page.
1. Plaatsingsvolgorde. U wordt omgeleid naar de pagina met succesmeldingen.
1. Ga terug naar PayPal/express/review/Page.
1. Klik op de knop **Opdracht plaatsen** knop.

<u>Verwachte resultaten</u>:

Er wordt slechts één bestelling gemaakt.

<u>Werkelijke resultaten</u>:

De volgende fout treedt op: *PayPal Express Checkout Token bestaat niet*, maar de tweede volgorde is correct geplaatst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
