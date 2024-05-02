---
title: Gebruikers die geen product aan winkelwagentje kunnen toevoegen als er niets is geselecteerd in Allow countries
description: Dit artikel bevat een patch voor de bekende Adobe Commerce 2.4.4 met PHP 8.1-uitgave, waarbij gebruikers geen producten aan het winkelwagentje kunnen toevoegen als de optie Landen toestaan is uitgeschakeld.
exl-id: d05d1956-de23-496c-9234-c461a3cfdf36
feature: Orders, Products, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
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

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de Commerce-beheerder.
1. Ga naar **Winkel** > **Configuratie** > **Algemeen** > **Landopties**
1. Selectie van alle opties ongedaan maken in **Landen toestaan** veld.
1. Klikken **Config opslaan** om de configuratie op te slaan.
1. Ga naar de winkel en probeer een product aan de winkelwagentje toe te voegen.

<u>Verwacht resultaat:</u>

U kunt een product aan de kar toevoegen.

<u>Werkelijk resultaat:</u>

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

De Adobe Commerce-configuratie wordt opgehaald `null` als een multiselect configuratie geen geselecteerde punten heeft. Deze configuratie als verder succesvol verwerkt in PHP versies ouder dan 8.1. In PHP 8.1 werkt het echter niet correct vanwege de fouten die worden veroorzaakt door de id[Null-tot niet-nullable argumenten van interne functies in PHP 8.1 afgekeurd](https://wiki.php.net/rfc/deprecate_null_to_scalar_internal_arg)&quot;.

## Oplossingen

Pas de volgende patch toe om het probleem op te lossen:

[AC-2655_2.4.4.patch.zip](assets/AC-2655_2.4.4.patch.zip)

## Hoe de pleister aanbrengen

Zie [Een door Adobe Commerce geleverde componentpatch toepassen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze kennisbasis voor ondersteuning voor instructies.

## Nuttige koppelingen

[Aangepaste patches op Adobe Commerce toepassen op cloudinfrastructuur](https://devdocs.magento.com/guides/v2.3/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.
