---
title: 'Vertexadres opschonen: verschillende adressen niet toegestaan'
description: Dit artikel praat over de oplossing voor de kwestie waar wanneer de gebruiker probeert om **different* het factureren en het verschepen adres in te gaan, met de toegelaten bevestiging van het adresbevestiging van de top, de opslag niet de gebruiker het zal laten ingaan.
exl-id: a481b044-3b74-4792-abc6-249a182c49e1
feature: B2B, Orders, Shipping/Delivery, Checkout
role: Developer
source-git-commit: 7cf1167bce8cef51b206b6cc1d75214288f9cb1c
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Vertexadres opschonen: verschillende adressen niet toegestaan

Dit artikel spreekt over de oplossing voor de kwestie waar wanneer de gebruiker probeert om a **verschillend** het factureren en het verschepen adres in te gaan, met toegelaten de adrevalidatie van het hoekpunt, zal de storefront niet de gebruiker het laten ingaan.

## Betrokken producten en versies

* Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.5-p1

## Probleem

<u> Stappen om </u> te reproduceren:

1. Ga naar Admin > **Opslag** > **Configuratie** > **Verkoop** > **het Schoonmaken van het Adres**.
1. Selecteer *Toegelaten* van **Reiniging van het Adres van het Punt van het Gebruik** drop-down en **sparen Config**.
1. Ga naar de frontend als gast en voeg een product aan de kar toe.
1. Klik op het pictogram van het Kunst en **ga aan Controle**.
1. Vul de adresvelden in.
1. Selecteer gewenste **Verzendmethode** en klik **daarna**.
1. Klik opnieuw op de **Volgende** knoop.
1. Uncheck **Mijn het factureren en het verschepen adres** **is het zelfde**, en ga een nieuw het facturerings adres (verschillend aan Adres) in.
1. Klik de **knoop van de Update**, dan klik **adres van de Update**.

<u> Verwachte resultaten </u>:

De gebruiker ziet verschillende factuuradres en verzendadressen.

<u> Ware resultaten </u>:

Wanneer de gebruiker op de update tikt, worden de facturerings- en verzendadressen weer gelijk.

## Oorzaak

Verificatie van hoekpuntadres is mislukt.

## Oplossing

Schakel de verificatie van hoekpuntadressen uit of voer een upgrade uit naar 2.4.0.

## Gerelateerde lezing

* [Bekende uitgave van Adobe Commerce 2.4.0: Foutbericht dat lokale betalingsmethode selecteert die in sommige landen wordt weergegeven tijdens het afrekenen](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0 B2B Admin kan geen configureerbaar product toevoegen om te citeren](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Betalingsmethoden van Braintree worden niet weergegeven bij de afhandeling van meerdere adressen](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekende uitgave van Adobe Commerce 2.4.0 - Vernieuwen van de activiteiten van de Klant werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0 - Export Tax Rates werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: &quot;Selecties toevoegen aan mijn winkelwagentje&quot; werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: ontbrekend label &quot;Resund&quot; in Klarna](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: er ontbreken twee knoppen op de pagina Nieuwe bestelling maken in Admin](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: wanneer Braintree is ingeschakeld, geeft Venmo een gedeeltelijke factuur af](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Foutbericht dat lokale betalingsmethode selecteert die in sommige landen wordt weergegeven tijdens het afrekenen](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Amazon Pay ingeschakeld, betalingsmethoden ontbreken wanneer Terug naar standaardafhandeling wordt gebruikt](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: 2.4.0-installatie mislukt met verouderde opslagcache](/help/troubleshooting/installation-and-upgrade/magento-2-4-0-known-issue-2-4-0-installation-fails-with-outdated-stores-cache.md)
