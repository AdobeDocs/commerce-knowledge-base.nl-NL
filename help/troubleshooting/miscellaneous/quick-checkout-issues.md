---
title: Problemen met snelle afhandeling oplossen
description: In dit artikel worden de problemen uitgelegd die u kunt ondervinden bij het gebruik van de extensie Quick Checkout voor Adobe Commerce en worden oplossingen geboden om deze problemen op te lossen zodat u de extensie kunt gebruiken.
exl-id: 8ab46318-d62a-4b7e-bbe5-4c52cfeb9e36
feature: Checkout, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Problemen met snelle afhandeling oplossen

In dit artikel worden de problemen uitgelegd die u kunt ondervinden bij het gebruik van de extensie Quick Checkout voor Adobe Commerce en worden oplossingen geboden om deze problemen op te lossen zodat u de extensie kunt gebruiken.

## Betrokken producten en versies

* De [Snelle afhandeling](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/overview.html) is compatibel met zowel Magento Open Source als Adobe Commerce. Zie [Levenscyclusbeleid](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html) voor meer informatie over ondersteunde versies.

## Onjuiste Composer-sleutels en minimale stabiliteit voor `RC`

<u>Oorzaak</u>:

Als het volgende foutbericht wordt weergegeven, hebt u mogelijk onjuiste composer-toetsen:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

<u>Oplossing</u>:

Controleer of uw componentsleutels zijn gekoppeld aan de _Magento-id_ worden gebruikt tijdens de registratie voor snelle afhandeling.

Om te zien welke componentensleutels worden gevormd:

1. Zoek de locatie van het dialoogvenster `auth.json` bestand:

   ```bash
   composer config --global home
   ```

1. De weergave `auth.json` bestand:

   ```bash
   cat /path/to/auth.json
   ```

1. Zie [welke toetsen aan uw Magento-id zijn gekoppeld](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

1. Minimale stabiliteit instellen op `RC` in de `composer.json` bestand.

   ```json
   "minimum-stability": "RC"
   ```

## Onvoldoende geheugen voor PHP

<u>Oorzaak</u>:

Als je het volgende foutbericht ziet, heb je onvoldoende geheugen voor PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

<u>Oplossing</u>:

[De geheugenlimiet verhogen](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) voor PHP op uw omgeving `php.ini`.

U kunt ook de geheugenlimiet opgeven met deze opdracht: `php -d memory_limit=-1 [path to composer]/composer require magento/quick-checkout`.

Bijvoorbeeld:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/quick-checkout
```

## Straaladreslijnen toevoegen met een nieuw verzendadres

Er is een bekend probleem met de extensie Snelle afhandeling.

Wanneer u [aanmelden met een Bolt-account](https://help.bolt.com/shoppers/guides/checkout/log-in/), kunt u een nieuw verzendadres toevoegen met een maximum van 4 regels per adres.

Als het nieuwe verzendadres meer dan 4 regels bevat, worden deze niet opgeslagen.

Adobe Commerce kan doorgaans worden geconfigureerd voor ondersteuning van maximaal 20 adreslijnen op straat.

## Onverwacht gedrag wanneer `Display Billing Address On` is ingesteld op `payment page`

Er is een bekend probleem met de extensie Snelle afhandeling.

Als u de `Display Billing Address On` aan de `payment page` en [aanmelden met een Bolt-account](https://help.bolt.com/shoppers/guides/checkout/log-in/) wanneer u de `My billing and shipping address are the same` selectievakje, het keuzerondje wordt weergegeven `use existing card`. Aangezien het factuuradres alleen van toepassing is op nieuwe creditcards, is het adres pas zichtbaar wanneer de gebruiker van de bout besluit een nieuwe creditcardoptie toe te voegen.

Zie de [Afhandeling](https://docs.magento.com/user-guide/configuration/sales/checkout.html) onderwerp voor meer informatie over `Display Billing Address On` parameter.
