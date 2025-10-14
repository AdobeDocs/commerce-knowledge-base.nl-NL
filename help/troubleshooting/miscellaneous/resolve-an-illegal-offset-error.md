---
title: Een ongeldige verschuivingsfout oplossen
description: Dit artikel biedt een oplossing voor het geval dat u in Adobe Commerce 2.1 of hoger een fout met betrekking tot een ongeldige offset ontvangt wanneer u een nieuw product maakt in Commerce Admin.
exl-id: 62d16d3c-7f4b-45e9-ae4b-fe2b58cc3620
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Een ongeldige verschuivingsfout oplossen

Dit artikel biedt een oplossing voor het geval dat u in Adobe Commerce 2.1 of hoger een fout met betrekking tot een ongeldige offset ontvangt wanneer u een nieuw product maakt in Commerce Admin.

Bij het maken van een nieuw product in Commerce Admin in Adobe Commerce 2.1 of hoger kan de volgende fout worden weergegeven:

```text
Warning: Illegal string offset 'is_in_stock' in [...]/vendor/
magento/module-catalog-inventory/Ui/DataProvider/Product/Form/
Modifier/AdvancedInventory.php on line 87
```

## Detail

Adobe Commerce 2.1 en hoger gebruiken PHP-codeopmerkingen in de `getDocComment` validatieaanroep in de [`getExtensionAttributes` &#x200B;](https://github.com/magento/magento2/blob/2.3/lib/internal/Magento/Framework/Api/ExtensionAttributesFactory.php#L64-L73) -methode in `Magento\Framework\Api\ExtensionAttributesFactory.php` .

Als u de PHP OPcache (die we aanbevelen) hebt ingeschakeld, wordt deze fout weergegeven omdat standaard de OPcache-instelling [`opcache.save_comments` &#x200B;](http://php.net/manual/en/opcache.configuration.php#ini.opcache.save_comments) is uitgeschakeld.

## Workaround

Zoek de configuratie-instellingen voor OPcache op en schakel `opcache.save_comments` als volgt in om dit probleem op te lossen:

### Stap 1: Zoek uw configuratie OPcache

#### U kunt als volgt de configuratie-instellingen voor OPcache vinden:

PHP OPcache-instellingen bevinden zich doorgaans in `php.ini` of `opcache.ini` . De locatie kan afhankelijk zijn van uw besturingssysteem en PHP-versie. Het OPcache-configuratiebestand heeft mogelijk een `[opcache]` -sectie of instellingen, zoals `opcache.enable` .

Gebruik de volgende richtlijnen om het te vinden:

* Apache-webserver:<br>

Voor Ubuntu met Apache bevinden de OPcache-instellingen zich doorgaans in `php.ini` .<br>
Voor CentOS met Apache of nginx bevinden de OPcache-instellingen zich doorgaans in `/etc/php.d/opcache.ini` .<br>
Als niet, gebruik het volgende bevel om van het de plaats te bepalen:

```bash
    $ sudo find / -name 'opcache.ini'
```

* nginx webserver met PHP-FPM: `/etc/php5/fpm/php.ini` .

Als u meer dan één `opcache.ini` hebt, wijzigt u ze allemaal.


### Stap 2: Inschakelen `opcache.save_comments`

1. Open het OPcache-configuratiebestand in een teksteditor.
1. Zoek `opcache.save_comments` en verwijder indien nodig de commentaarmarkering.
1. Controleer of de waarde is ingesteld op `1` .
1. Sla de wijzigingen op en sluit de teksteditor af.
1. Start de webserver opnieuw:

   * Apache, Ubuntu: `service apache2 restart`
   * Apache, CentOS: `service httpd restart`
   * nginx, Ubuntu en CentOS: `service nginx restart`

1. Regenereer DI-configuratie en alle ontbrekende klassen die automatisch kunnen worden gegenereerd:

```bash
    $ bin/magento setup:di:compile`
```
