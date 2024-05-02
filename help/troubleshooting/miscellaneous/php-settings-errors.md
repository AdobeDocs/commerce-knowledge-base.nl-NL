---
title: Fouten in PHP-instellingen
description: Dit artikel bevat oplossingen voor fouten met PHP-instellingen.
exl-id: 51fb3c95-2e25-4d86-a6cf-e08e90d097ca
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Fouten in PHP-instellingen

Dit artikel bevat oplossingen voor fouten met PHP-instellingen.

## Fout in PHP-geheugenlimiet

De gereedheidscontroles zorgen ervoor dat er minstens 1 GB geheugen is gereserveerd voor PHP-processen. Deze instelling moet voldoende zijn voor de meeste installaties, inclusief het installeren van optionele voorbeeldgegevens. Nochtans, adviseren wij minstens 2 GB voor het zuiveren.

De limiet voor PHP-geheugen verhogen:

1. Meld u aan bij uw Adobe Commerce-server.
1. Zoek uw `php.ini` bestand met de volgende opdracht:

   ```
   bash    $ php --ini
   ```

1. Als gebruiker met `root` rechten, gebruik een teksteditor om de `php.ini` gespecificeerd door `Loaded Configuration File`.
1. Zoeken `memory_limit`.
1. Wijzig deze in een waarde van `2GB` voor normaal gebruik en foutopsporing.
1. Sla uw wijzigingen op in `php.ini` en sluit de teksteditor af.
1. Start de webserver opnieuw. Hieronder volgen voorbeelden:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`
   * nginx (zowel CentOS als Ubuntu): `service nginx restart`

1. Probeer de installatie opnieuw.

## max-input-vars fout door grote vormen

Configuraties met een groot aantal weergaven, producten, kenmerken of opties kunnen formulieren genereren die de vooraf ingestelde limiet voor PHP overschrijden. Als het aantal verzonden waarden de `max-input-vars` limiet die binnen `php.ini` (standaard is 1000), worden de resterende gegevens niet overgedragen en worden deze databasewaarden niet bijgewerkt. Als dit gebeurt, verschijnt er een waarschuwing in het PHP log:

```terminal
PHP message: PHP Warning: Unknown: Input variables exceeded 1000. To increase the limit change max_input_vars in php.ini.
```

Er is geen eigenlijke waarde voor `max-input-vars`; dit hangt af van de grootte en complexiteit van uw configuratie. Wijzig de waarde in het dialoogvenster `php.ini` bestand naar wens. Zie [Vereiste PHP-instellingen](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html).

## fout bij nesten van maximale functie xdebug

Zie [Fouten in het nestniveau van maximumfuncties tijdens de installatie opsporen](/help/troubleshooting/miscellaneous/installation-xdebug-maximum-function-nesting-level-error.md).

## Fouten worden weergegeven wanneer u een PHTML-sjabloon opent

Fouttekst is doorgaans:

```terminal
Parse error: syntax error, unexpected 'data' (T_STRING)
```

### Oplossing: instellen `asp_tags = off` in php.ini

Meerdere sjablonen hebben syntaxis voor ondersteuning van abstract niveau op sjablonen (gebruik verschillende sjabloonengines, zoals Twig) die zijn opgenomen in `<% %>` tags, zoals in [template](https://github.com/magento/magento2/blob/2.0/app/code/Magento/Catalog/view/adminhtml/templates/product/edit/base_image.phtml) voor het weergeven van een productafbeelding:

```php
<img
    class="product-image"
    src="<%- data.url %>"
    data-position="<%- data.position %>"
    alt="<%- data.label %>" />
```

Meer informatie over [asp\_tags](http://php.net/manual/en/ini.core.php#ini.asp-tags).

Bewerken `php.ini` en instellen `asp_tags = off`. Zie voor meer informatie [Vereiste PHP-instellingen](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html).
