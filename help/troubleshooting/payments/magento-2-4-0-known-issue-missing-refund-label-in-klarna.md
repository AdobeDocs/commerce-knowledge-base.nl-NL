---
title: 'Bekende uitgave van ''Adobe Commerce 2.4.0: ontbrekend label ''Refund'' in Klarna'
description: Dit artikel biedt een oplossing voor een bekend probleem in Admin voor een ontbrekend **Refund**-label in Klarna VBE (Bundled Extension van leverancier). Wanneer in het portaal Klarna een restitutie wordt uitgevoerd, wordt het label **Resund** niet weergegeven naast het product uit de bundel dat is terugbetaald.
exl-id: f08039b2-7f8b-481e-8ec8-1659e227744f
feature: B2B, Orders, Payments
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Bekende uitgave van Adobe Commerce 2.4.0: ontbrekend label &quot;Resund&quot; in Klarna

Dit artikel verstrekt een alternerende actie voor een bekende kwestie in Admin voor een ontbrekend **Terugkeer** etiket in Klarna VBE (de Gebundelde Uitbreiding van de Leverancier). Wanneer in het Klarna portaal die een restitutie leiden, wordt het **terugbetaalde** etiket niet getoond naast het Gebundelde product dat werd teruggegeven.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.0
* Adobe Commerce over cloudinfrastructuur 2.4.0

## Probleem

<u> Eerste vereisten:</u>

* Klarna is ingeschakeld.
* Er wordt een gebundeld product gemaakt.

<u> Stappen om te reproduceren </u>

1. Ga naar Adobe Commerce vooraf:sturen, en voeg een Gebundeld product aan **kar** toe.
1. Navigeer naar de kassa.
1. De informatie van de consument van de input in controle en klik **daarna**.
1. Selecteer **optie KP** en klik **de Orde van de Plaats**.
1. Ga naar **Admin** > **Verkoop** > **Orden**.
1. Open de volgorde.
1. Factuur maken voor product.
1. Ga naar **Facturen** > **Uitgezochte factuur** > klik **Memo van het Krediet** > klik **Terugkeren** (niet **Offline teruggeven**).
1. Ga naar Klarna portal.
1. Open de volgorde.
1. Het **terugbetaalde** etiket is aanwezig.

<u> Verwacht resultaat </u>

Op het Klarna portaal, wordt het **Terugkeer** etiket getoond naast het product dat werd teruggegeven.

<u> Werkelijk resultaat </u>

Op het Klarna portaal, wordt het **Terugkeer** etiket niet getoond naast het product dat werd teruggegeven.

## Workaround

De oplossing voor deze kwestie moet het ontbrekende **teruggeven** etiket in het portaal Klarna voor teruggegeven gebundelde gebundelde producten negeren. De terugbetaling is voorgekomen, alhoewel het **terugbetaalde** etiket niet toonde. Het probleem zal naar verwachting worden opgelost in Adobe Commerce 2.4.1, dat in het vierde kwartaal van 2020 zal worden gepubliceerd.

## Gerelateerde lezingen in onze kennisbasis voor ondersteuning:

* [Bekende uitgave van Adobe Commerce 2.4.0: onbewerkte weergave van berichtgegevens op winkel](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Export Tax Rates werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Betalingsmethoden voor Braintree worden niet weergegeven bij de afhandeling van meerdere adressen](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Foutbericht dat lokale betalingsmethode selecteert die in sommige landen wordt weergegeven tijdens het afrekenen](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: 404-fout bij het verwijderen van beloningspunten bij afhandeling via meerdere verzendingen](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: weergavefout voor bestellingen](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B Admin kan geen configureerbaar product toevoegen om te citeren](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Bekende uitgave van Adobe Commerce 2.4.0 - Vernieuwen van de activiteiten van de Klant werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: &quot;Selecties toevoegen aan mijn winkelwagentje&quot; werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
