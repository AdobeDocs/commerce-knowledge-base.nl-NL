---
title: Fouten in PHP-instellingen
description: Dit artikel bevat oplossingen voor fouten met PHP-instellingen.
exl-id: 51fb3c95-2e25-4d86-a6cf-e08e90d097ca
feature: Configuration
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
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
1. Zoek het `php.ini` -bestand met de volgende opdracht:

   ```
   bash    $ php --ini
   ```

1. Als gebruiker met `root` bevoegdheden gebruikt u een teksteditor om de `php.ini` opgegeven door `Loaded Configuration File` te openen.
1. Zoek `memory_limit` .
1. Wijzig deze in de waarde `2GB` voor normaal gebruik en foutopsporing.
1. Sla de wijzigingen in `php.ini` op en sluit de teksteditor af.
1. Start de webserver opnieuw. Hieronder volgen voorbeelden:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`
   * nginx (zowel CentOS als Ubuntu): `service nginx restart`

1. Probeer de installatie opnieuw.

## max-input-vars fout door grote vormen

Configuraties met een groot aantal weergaven, producten, kenmerken of opties kunnen formulieren genereren die de vooraf ingestelde limiet voor PHP overschrijden. Als het aantal verzonden waarden de `max-input-vars` -limiet overschrijdt die is ingesteld binnen `php.ini` (de standaardwaarde is 1000), worden de resterende gegevens niet overgedragen en worden die databasewaarden niet bijgewerkt. Als dit gebeurt, verschijnt er een waarschuwing in het PHP log:

```bash
PHP message: PHP Warning: Unknown: Input variables exceeded 1000. To increase the limit change max_input_vars in php.ini.
```

Er is geen &#39;juiste&#39; waarde voor `max-input-vars`; deze is afhankelijk van de grootte en complexiteit van uw configuratie. Wijzig desgewenst de waarde in het `php.ini` -bestand. Zie [ Vereiste PHP montages ](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html).

## fout bij nesten van maximale functie xdebug

Zie [ tijdens installatie, xdebug maximumfunctie die niveaufout ](/help/troubleshooting/miscellaneous/installation-xdebug-maximum-function-nesting-level-error.md) nest.

## Fouten worden weergegeven wanneer u een PHTML-sjabloon opent

Fouttekst is doorgaans:

```bash
Parse error: syntax error, unexpected 'data' (T_STRING)
```

### Oplossing: stel `asp_tags = off` in php.ini in

De veelvoudige malplaatjes hebben syntaxis voor steun abstract niveau op malplaatjes (gebruik verschillende malplaatjemotoren zoals Twig) verpakt in `<% %>` markeringen, als dit [ malplaatje ](https://github.com/magento/magento2/blob/2.0/app/code/Magento/Catalog/view/adminhtml/templates/product/edit/base_image.phtml) voor het tonen van een productbeeld:

```php
<img
    class="product-image"
    src="<%- data.url %>"
    data-position="<%- data.position %>"
    alt="<%- data.label %>" />
```

Meer informatie over [ asp\_tags ](http://php.net/manual/en/ini.core.php#ini.asp-tags).

Bewerken `php.ini` en instellen `asp_tags = off` . Voor meer informatie, zie [ Vereiste PHP montages ](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html).
