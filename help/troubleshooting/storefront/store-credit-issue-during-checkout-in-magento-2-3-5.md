---
title: Probleem met winkelcreditering tijdens afhandeling in Adobe Commerce 2.3.5
description: Dit artikel biedt een oplossing voor het bekende probleem met winkelkrediet tijdens het afrekenen in Adobe Commerce 2.3.5, waar kopers fouten krijgen tijdens het afrekenen na het selecteren en later verwijderen van het gebruik van winkelkredieten. In Adobe Commerce 2.3.6 is een permanente oplossing beschikbaar.
exl-id: a0cca226-4d95-40b3-bd37-f13d28591366
feature: Checkout, Orders, Storefront
role: Admin
source-git-commit: b3d39e6b02728f05f046adf7be94ffacbca944d5
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---

# Probleem met winkelcreditering tijdens afhandeling in Adobe Commerce 2.3.5

Dit artikel biedt een oplossing voor het bekende probleem met winkelkrediet tijdens het afrekenen in Adobe Commerce 2.3.5, waar kopers fouten krijgen tijdens het afrekenen na het selecteren en later verwijderen van het gebruik van winkelkredieten. In Adobe Commerce 2.3.6 is een permanente oplossing beschikbaar.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.3.5
* Adobe Commerce over wolkeninfrastructuur 2.3.5

## Probleem

<u> Stappen om </u> te reproduceren:

1. De klant voegt producten aan de kar toe en gaat verder met de afhandeling.
1. Klant geeft krediet op als betalingsmethode.
1. De Klant verwijdert winkelkrediet en wijzigt de betalingsmethode.
1. De klant gaat door met het afrekenen.

<u> Verwachte resultaten </u>:

Alle ordegegevens worden correct weergegeven.

<u> Ware resultaten </u>:

Adobe Commerce geeft een fout weer in de sectie Overzicht van bestellingen op de pagina Volgorde.

## Oplossing

Klanten kunnen de pagina Volgorde vernieuwen en de gegevens in het overzicht van bestellingen worden correct geladen. Een oplossing is beschikbaar in Adobe Commerce 2.3.6, dat volgens de planning in het vierde kwartaal van 2020 zal worden uitgebracht.

## Gerelateerde lezing

Artikelen voor Adobe Commerce 2.3.5 bekende problemen in onze basis voor ondersteunende kennis:

* [Opdrachten voor meerdere verzendingen met een virtueel product worden niet correct verwerkt in Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)

* [Bulkactie product count known issue in Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)

* [Probleem met afhandeling van afhandeling voor Amazon Pay in Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

* [Probleem met productvergelijking in Adobe Commerce 2.3.5](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)

In onze documentatie voor ontwikkelaars:

* [ Adobe Commerce 2.3.5 Bekende Kwesties ](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
