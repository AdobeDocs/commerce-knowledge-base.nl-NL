---
title: 'Adobe Commerce 2.4.0 patch: retourneert aanmaakprobleem voor verzendlabel'
description: Dit artikel bevat een patch voor het bekende Adobe Commerce 2.4.0-probleem wanneer er een probleem is met het afdrukken van een verzendlabel voor geretourneerde meldingen van klanten.
exl-id: f78f8d7e-29e9-4d6c-83f6-cd5afa1d7d9c
feature: B2B, Orders, Returns, Communications, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Adobe Commerce 2.4.0-patch: retourneert probleem met aanmaak van verzendlabel

Dit artikel bevat een patch voor het bekende Adobe Commerce 2.4.0-probleem wanneer er een probleem is met het afdrukken van een verzendlabel voor geretourneerde meldingen van klanten.

## Betrokken producten en versies

* Adobe Commerce over cloudinfrastructuur 2.4.0
* Adobe Commerce op locatie 2.4.0

## Probleem

<u>Stappen om te reproduceren:</u>

1. Plaats en voltooi een bestelling met een van de volgende kernverzendmethoden: FedEx, DHL, UPS en USPS.
1. Hiermee maakt u geretourneerde waarden voor deze bestelling en autoriseert u deze.
1. Een geautoriseerde **Retourinformatie** pagina en klik op de knop **Verzendlabel maken** knop.
1. Selecteer de verzendmethode, voeg een product toe aan een pakket en klik op Opslaan.

<u>Verwacht resultaat:</u>

Er is een verzendlabel gemaakt en er verschijnt een bericht: *Je hebt een verzendlabel gemaakt.*

<u>Werkelijk resultaat:</u>

De **Retourinformatie** De pagina is verbroken en er verschijnt een foutbericht op de pagina Retourgegevens: *Algemene informatie Er zijn wijzigingen aangebracht in deze sectie die niet zijn opgeslagen. Dit tabblad bevat ongeldige gegevens*.

## Oplossing

Toepassen [pleister](assets/MC-35984-2.4.0-CE-composer.patch.zip) in dit artikel.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[MC-35984-2.4.0-CE-composer.patch](assets/MC-35984-2.4.0-CE-composer.patch.zip)

De patch is ook beschikbaar voor beide toepassingen, `.git` en `.composer`, indelingen op [Adobe Commerce-downloads](https://magento.com/tech-resources/download) pagina, onder **Patches** in de linkerkolomnavigatie. Zoeken naar MC-35984-patch.

## Hoe de pleister aanbrengen

Zie voor instructies [Hoe een door Adobe geleverde componentpleister aanbrengen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze pagina van de steunkennis.

## Gerelateerde lezingen in onze kennisbasis voor ondersteuning:

* [Bekende uitgave van Adobe Commerce 2.4.0: onbewerkte weergave van berichtgegevens op winkel](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Export Tax Rates werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: &quot;Selecties toevoegen aan mijn winkelwagentje&quot; werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Betalingsmethoden voor Braintree worden niet weergegeven bij de afhandeling van meerdere adressen](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0 B2B Admin kan geen configureerbaar product toevoegen om te citeren](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: weergavefout voor bestellingen](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Aanmaak van verzendlabels Bekend probleem in Adobe Commerce 2.4.0](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
