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

Dit artikel verstrekt een oplossing voor een bekende kwestie in Adobe Commerce 2.4.0 voor a &quot;*404 niet Gevonden*&quot;Web-pagina fout wanneer het verwijderen van beloningspunten op een multi-verschepende controlepagina. Momenteel, op de multi-verschepende checkout pagina, wanneer het proberen om beloningspunten te verwijderen die werden gebruikt om voor een orde te betalen, wordt de pagina van a &quot;*404 niet Gevonden* &quot; getoond in plaats van succesvolle prijspunten annulering. Dit probleem wordt opgelost in een Adobe Commerce 2.4.1-patch-release.

## Betrokken producten en versies

* Adobe Commerce 2.4.0 (alle implementatiemethoden)

## Probleem

<u> Stappen om te reproduceren </u>

1. Navigeer naar de winkel en meld u aan als klant.
1. Voeg minstens twee producten aan **toe die Kar Shopping**.
1. Open **mini-Kar**.
1. Klik de **Mening en geef de verbinding van de Kar** uit.
1. Klik de **Controle uit met Veelvoudige Adressen** verbinding.
1. Selecteer verzendadressen op de **verschepen naar Veelvoudige Adressen** pagina.
1. Klik **gaan naar de Verzendinformatie** knoop.
1. Selecteer het **Vaste Tarief - Vaste Verzendmethode** voor elk adres.
1. Klik **blijven aan de knoop van de Informatie van het Factureren**.
1. Controleer het **Gebruik Uw Betrouwbare Punten** checkbox op de **Facturerende Informatie** pagina.
1. Klik **gaan uw Orde** knoop herzien.
1. Klik **verwijderen** verbinding voor om het even welk adres om de beloningspunten te verwijderen.

<u> Verwachte resultaten </u>

* De **Shopping Kart** pagina zou moeten verschijnen.
* &quot;*u verwijderde de beloningspunten uit deze orde.*&quot; moet worden weergegeven.

<u> Werkelijk resultaat </u>

A &quot;*404 niet Gevonden*&quot;foutenpagina verschijnt.

## Workaround

De oplossing moet de koper hebben terug naar **Kar** navigeren en de beloningspunten van de **Kar** Web-pagina verwijderen. Het probleem zal naar verwachting worden opgelost in de Adobe Commerce versie 2.4.1-patch, die in het vierde kwartaal van 2020 zal worden uitgebracht.

## Gerelateerde lezing

* [Bekende uitgave van Adobe Commerce 2.4.0 - Vernieuwen van de activiteiten van de Klant werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Onbewerkte weergave van berichtgegevens op Storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: belastingtarieven voor export werken niet](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B Admin kan geen configureerbaar product toevoegen om te citeren](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: weergavefout voor bestellingen](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
