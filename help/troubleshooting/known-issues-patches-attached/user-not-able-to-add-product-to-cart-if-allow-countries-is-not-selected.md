---
title: Gebruikers die geen product aan winkelwagentje kunnen toevoegen als er niets is geselecteerd in Allow countries
description: Dit artikel bevat een patch voor de bekende Adobe Commerce 2.4.4 met PHP 8.1-uitgave, waarbij gebruikers geen producten aan het winkelwagentje kunnen toevoegen als de optie Landen toestaan is uitgeschakeld.
exl-id: d05d1956-de23-496c-9234-c461a3cfdf36
feature: Orders, Products, Shopping Cart
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Gebruikers die geen product aan winkelwagentje kunnen toevoegen als er niets is geselecteerd in Allow countries

Dit artikel bevat een patch voor de bekende Adobe Commerce 2.4.4 met PHP 8.1-uitgave, waarbij gebruikers geen producten aan het winkelwagentje kunnen toevoegen als de optie Landen toestaan is uitgeschakeld.

## Betrokken producten en versies

Adobe Commerce 2.4.4 met PHP 8.1

## Probleem

Gebruikers kunnen geen producten aan het winkelwagentje toevoegen als de optie Landen toestaan is uitgeschakeld.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij de Commerce-beheerder.
1. Ga naar **Opslag** > **Configuratie** > **Algemeen** > **Opties van het Land**
1. Deselecteer alle opties op **toestaat Landen** gebied.
1. Klik **sparen Config** om de configuratie te bewaren.
1. Ga naar de winkel en probeer een product aan de winkelwagentje toe te voegen.

<u> Verwacht Resultaat:</u>

U kunt een product aan de kar toevoegen.

<u> Ware Resultaat:</u>

U kunt geen product aan de kar toevoegen. U krijgt de volgende consolefout:

```bash
Failed to load resource: the server responded with a status of 400 (Bad Request)
customer-data.js:87 Uncaught Error: [object Object]
    at Object.<anonymous> (customer-data.js:87:23)
    at fire (jquery.js:3500:50)
    at Object.fireWith [as rejectWith] (jquery.js:3630:29)
    at done (jquery.js:9798:30)
    at XMLHttpRequest.<anonymous> (jquery.js:10057:37)
```

## Oorzaak

De Adobe Commerce-configuratie haalt `null` op als een multiselect-configuratie geen geselecteerde items heeft. Deze configuratie als verder succesvol verwerkt in PHP versies ouder dan 8.1. Nochtans in PHP 8.1 werkt het niet behoorlijk toe te schrijven aan de fouten die door &quot;[ worden veroorzaakt verval ongeldig overgaan tot niet-nullable argumenten van interne functies in PHP 8.1 ](https://wiki.php.net/rfc/deprecate_null_to_scalar_internal_arg)&quot;.

## Oplossingen

Pas de volgende patch toe om het probleem op te lossen:

[AC-2655_2.4.4.patch.zip](assets/AC-2655_2.4.4.patch.zip)

## Hoe de pleister aanbrengen

Zie [ hoe te om een componentenflard toe te passen die door Adobe Commerce ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze steunkennisbasis voor instructies wordt verstrekt.

## Nuttige koppelingen

[ pas douaneflarden op Adobe Commerce op wolkeninfrastructuur ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaardocumentatie toe.
