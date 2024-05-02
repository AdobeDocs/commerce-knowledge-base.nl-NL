---
title: "Adobe Commerce 2.4.0: 404 error removing rewards on multi-Shipping checkout"
description: Dit artikel biedt een oplossing voor een bekende uitgave in Adobe Commerce 2.4.0 voor een fout op de webpagina "*404 Niet gevonden*"" wanneer u beloningspunten verwijdert op een pagina voor multiverzending. Op de pagina voor afhandeling van meerdere verzendingen wordt op dit moment een pagina "*404 Niet gevonden*" weergegeven in plaats van een geslaagde annulering van bonuspunten. Deze pagina is bedoeld om bonuspunten te verwijderen die zijn gebruikt om een bestelling te betalen. Dit probleem wordt opgelost in een Adobe Commerce 2.4.1-patch-release.
exl-id: 59de4b3d-af28-4ae8-8f55-4ec958e6ee8b
feature: B2B, Checkout, Orders, Rewards, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: 404-fout: beloningspunten verwijderen bij afhandeling via meerdere verzendingen

Dit artikel biedt een oplossing voor een bekende uitgave in Adobe Commerce 2.4.0 voor een &quot;*404 Niet gevonden*&quot;-webpaginafout bij het verwijderen van beloningspunten op een pagina voor afhandeling via meerdere verzendingen. Op de pagina voor afhandeling van meerdere verzendingen wordt momenteel een &#39;*404 Niet gevonden* De pagina wordt weergegeven in plaats van de annulering van bonuspunten. Dit probleem wordt opgelost in een Adobe Commerce 2.4.1-patch-release.

## Betrokken producten en versies

* Adobe Commerce 2.4.0 (alle implementatiemethoden)

## Probleem

<u>Stappen om te reproduceren</u>

1. Navigeer naar de winkel en meld u aan als klant.
1. Voeg ten minste twee producten toe aan de **Winkelwagentje**.
1. Open de **Mini-Cart**.
1. Klik op de knop **Winkelwagentje weergeven en bewerken** koppeling.
1. Klik op de knop **Uitchecken met meerdere adressen** koppeling.
1. Verzendadressen selecteren op de **Verzenden naar meerdere adressen** pagina.
1. Klik op de knop **Ga naar Verzendgegevens** knop.
1. Selecteer de **Vaste prijs - Vaste verzendmethode** voor elk adres.
1. Klik op de knop **Doorgaan met factureringsgegevens** knop.
1. Controleer de **Uw punten voor beloningen gebruiken** Selectievakje op de **Factuurgegevens** pagina.
1. Klik op de knop **Ga naar Je bestelling bekijken** knop.
1. Klik op de knop **Verwijderen** link naar elk adres om de bonuspunten te verwijderen.

<u>Verwachte resultaten</u>

* De **Winkelwagentje** wordt weergegeven.
* De &quot;*Je hebt de bonuspunten uit deze bestelling verwijderd.* &#39;&#39; wordt weergegeven.

<u>Werkelijk resultaat</u>

A &quot;*404 Niet gevonden* &#39;&#39; wordt weergegeven.

## Workaround

De oplossing is dat de koper teruggaat naar de **Kar** en de bonuspunten uit de **Kar** webpagina. Het probleem zal naar verwachting worden opgelost in de Adobe Commerce versie 2.4.1-patch, die in het vierde kwartaal van 2020 zal worden uitgebracht.

## Gerelateerde lezing

* [Bekende uitgave van Adobe Commerce 2.4.0 - Vernieuwen van de activiteiten van de Klant werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Onbewerkte weergave van berichtgegevens op Storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: belastingtarieven voor export werken niet](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B Admin kan geen configureerbaar product toevoegen om te citeren](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: weergavefout voor bestellingen](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
