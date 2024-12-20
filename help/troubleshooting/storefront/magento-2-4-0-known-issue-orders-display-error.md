---
title: 'Bekende uitgave van Adobe Commerce 2.4.0: weergavefout voor bestellingen'
description: 'Dit artikel biedt een oplossing voor een bekende uitgave in Adobe Commerce voor een weergavefout voor bestellingen. Wanneer aangemelde klanten hun bestellingen controleren in het menu **Mijn account** (**Mijn account&gt; Mijn bestellingen**), kan het orderenraster het aantal bestellingen per pagina niet wijzigen van pagina 2 naar 20 als er 11 bestellingen zijn. Ook, als er meer orden zijn dan wordt gevormd om per pagina te tonen, wanneer het navigeren aan de laatste pagina met orden, produceert het veranderen van het aantal orden die per pagina worden getoond het foutenbericht: *U hebt geen orden* geplaatst. Dit probleem wordt opgelost in Adobe Commerce 2.4.1.'
exl-id: a6d300e1-1cbc-42b9-997d-d72f8765517b
feature: B2B, Categories, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# Bekende uitgave van Adobe Commerce 2.4.0: weergavefout voor bestellingen

Dit artikel biedt een oplossing voor een bekende uitgave in Adobe Commerce voor een weergavefout voor bestellingen. Wanneer het programma geopende klanten hun orden in het **Mijn menu van de Rekening** herzien (**Mijn Rekening > Mijn Orden**), is het ordensnet niet in staat om het aantal orden per pagina aan 20 van pagina 2 te schakelen wanneer er 11 orden zijn. Ook, als er meer orden zijn dan worden gevormd om per pagina te worden getoond, wanneer het navigeren aan de laatste pagina met orden, produceert het veranderen van het aantal orders per pagina het foutenbericht: *u hebt geen orden* geplaatst. Dit probleem wordt opgelost in Adobe Commerce 2.4.1.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.0
* Adobe Commerce over cloudinfrastructuur 2.4.0

## Probleem

<u> Eerste vereisten </u>

* Adobe Commerce 2.4.0 is geïnstalleerd.
* Maak ten minste één categorie en één eenvoudig product.

<u> Stappen om te reproduceren </u>

1. Maak 11 bestellingen met producten.
1. Ga naar **Mijn Rekening**.
1. Ga naar **Mijn Orden**.
1. Klik op de tweede pagina om de elfde volgorde weer te geven op het orderraster.
1. Selecteer **tonen = 20 per pagina** van het drop-down menu.

<u> Verwacht resultaat </u>

Alle elf bestellingen worden op de eerste pagina weergegeven, zoals u had verwacht.

<u> Werkelijk resultaat </u>

*u hebt geplaatst geen orden* foutenmelding wordt getoond.

## Workaround

De oplossing moet de koper hebben **Mijn Orden** pagina heropenen, en dan zal de ordenlijst correct worden getoond. Het probleem wordt opgelost in de volgende release, Adobe Commerce 2.4.1, die in het vierde kwartaal van 2020 wordt gepubliceerd.

## Gerelateerde lezingen in onze kennisbasis voor ondersteuning

* [Bekende uitgave van Adobe Commerce 2.4.0 - Vernieuwen van de activiteiten van de Klant werkt niet](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Onbewerkte weergave van berichtgegevens op Storefront](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: belastingtarieven voor export werken niet](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B Admin kan geen configureerbaar product toevoegen om te citeren](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
