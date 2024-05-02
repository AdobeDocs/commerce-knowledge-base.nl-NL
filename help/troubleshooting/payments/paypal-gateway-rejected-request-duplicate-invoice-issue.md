---
title: PayPal-gateway afgewezen aanvraag - dubbele factuurkwestie
description: Dit artikel bevat een oplossing voor de afgewezen aanvraag van de PayPal-gateway - dubbele factuurkwestie.
exl-id: b6c4ede1-97a5-4db3-9b05-ab979cf809b3
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# PayPal-gateway afgewezen aanvraag - dubbele factuurkwestie

Dit artikel bevat een oplossing voor de afgewezen aanvraag van de PayPal-gateway - dubbele factuurkwestie.

Bij het verzenden van de betaling zien klanten mogelijk een fout voor een dubbele factuur:

>De PayPal-gateway heeft het verzoek afgewezen. Er is al betaling verricht voor deze factuur (\#10412: Dubbele factuur)

De kwestie doet zich voor wanneer facturen met dezelfde id&#39;s meerdere keren naar PayPal worden verzonden.

U kunt dit probleem oplossen door meerdere betalingen per factuur toe te staan in de voorkeuren voor betalingen van PayPal. Als PayPal wordt gewijzigd, worden betalingen geaccepteerd zonder foutberichten, zelfs voor facturen met dubbele id&#39;s.

## Betrokken versies

* Adobe Commerce op locatie, alle versies
* Adobe Commerce op cloud-infrastructuur, alle versies

## Probleem

Bij het verzenden van de betaling zien klanten het foutbericht:

```
... main.CRITICAL: Exception message: PayPal gateway has rejected request. Payment has already been made for this InvoiceID (#10412: Duplicate invoice).
```

PayPal kan de betaling niet verwerken en de bestelling niet voltooien.

## Oorzaak

Het foutbericht wordt weergegeven wanneer facturen met dezelfde id meerdere keren naar PayPal worden verzonden.

Dit kan gebeuren wanneer dezelfde gegevens op verschillende Adobe Commerce-sites worden gebruikt (zelfs in de lokale en de parkeeromgeving). Bijzondere scenario&#39;s kunnen de volgende zijn:

* Meerdere winkels verzenden facturen naar PayPal en gebruiken dezelfde factuur-id&#39;s
* Een nieuwe winkel verzendt een factuur met een id die eerder door een oude winkel is verzonden

Standaard staat PayPal verwerking voor dezelfde factuur niet toe.

## Oplossing

Wijzig je PayPal-profiel om meerdere betalingen per factuur-ID toe te staan. Je moet deze wijzigingen aanbrengen via PayPal.

1. Meld u aan bij uw account op [https://www.paypal.com](https://www.paypal.com/).
1. Klikken **Profiel** > **Profiel en instellingen** (rechterbovenhoek).
1. Ga naar **Mijn verkooptools**.
1. Navigeren naar **Betaald krijgen en mijn risico beheren** > **Blokbetalingen** en klik op **Bijwerken**.
1. **Verkoopvoorkeuren**, klikt u op **Voorkeuren voor betalingsontvangst**.
1. Onder **Accidentele betalingen blokkeren**, kiest u **Nee, meerdere betalingen per factuur toestaan**.    ![paypal_allow_multiple_payments_per_factuur_id.png](assets/paypal_allow_multiple_payments_per_invoice_id.png)
1. Naar beneden schuiven en klikken **Opslaan**.

## Meer informatie

* [Onbedoelde betalingen blokkeren](https://developer.paypal.com/docs/admin/setup-account/#block-accidental-payments) op PayPal Developer Docs.
* PayPal-betalingen in onze gebruikershandleiding:
   * [PayPal Express-afhandeling](/docs/commerce-admin/stores-sales/payments/paypal/paypal-express-checkout.html)
   * [Andere PayPal-oplossingen](/docs/commerce-admin/stores-sales/payments/paypal/paypal.html)
* In onze documentatie voor ontwikkelaars:
   * [PayPal-betalingsmethoden instellen voor Adobe Commerce op cloudinfrastructuur](/docs/commerce-cloud-service/user-guide/configure-store/paypal.html)
   * [Betalingsintegratie](https://developer.adobe.com/commerce/php/development/payments-integrations/)
