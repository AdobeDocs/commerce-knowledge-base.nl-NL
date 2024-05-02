---
title: Fouten bij het installeren van optionele voorbeeldgegevens
description: Dit onderwerp bespreekt oplossingen aan fouten u het installeren van facultatieve steekproefgegevens zou kunnen ontmoeten.
exl-id: 14692e3a-188c-45f1-9df5-ac873cc9eff0
feature: Console, Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Fouten bij het installeren van optionele voorbeeldgegevens

Dit onderwerp bespreekt oplossingen aan fouten u het installeren van facultatieve steekproefgegevens zou kunnen ontmoeten.

## Symptom (bestandssysteemmachtigingen)

Fout in het consolelogboek tijdens de installatie van steekproefgegevens die de Tovenaar van de Opstelling gebruiken:

```php
Module 'Magento_CatalogRuleSampleData':
[ERROR] exception 'Magento\Framework\Exception\LocalizedException' with message 'Can't create directory /var/www/html/magento2/generated/code/Magento/CatalogRule/Model/.' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Generator.php:103

(more)

Next exception 'ReflectionException' with message 'Class Magento\CatalogRule\Model\RuleFactory does not exist' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Reader/ClassReader.php:29

(more)
```

Deze uitzonderingen zijn het gevolg van de machtigingsinstellingen van het bestandssysteem.

### Oplossing

[Eigendom en machtigingen van het bestandssysteem opnieuw instellen](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) als een gebruiker met `root` rechten.

## Symptom (productiemodus)

Als u momenteel bent ingesteld op [productiemodus](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html), de installatie van voorbeeldgegevens mislukt als u de [magento sampledata:implementeren](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/sample-data/composer-packages.html) opdracht:

```php
PHP Fatal error: Uncaught TypeError: Argument 1 passed to Symfony\Component\Console\Input\ArrayInput::__construct() must be of the type array, object given, called in /<path>/vendor/magento/framework/ObjectManager/Factory/AbstractFactory.php on line 97 and defined in /<path>/vendor/symfony/console/Symfony/Component/Console/Input/ArrayInput.php:37
```

### Oplossing

Installeer geen voorbeeldgegevens in de productiemodus. Overschakelen naar de modus Ontwikkelaar en enkele wissen `var` en probeer het opnieuw.

Voer de volgende opdrachten in in de volgorde als de [Adobe Commerce-eigenaar bestandssysteem](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/file-system/overview.html):

```php
cd <magento_root>
bin/magento deploy:mode:set developer
rm -rf generated/code/* generated/metadata/*
bin/magento sampledata:deploy
```

## Symptom (beveiliging)

Tijdens de installatie van optionele voorbeeldgegevens wordt een bericht weergegeven dat lijkt op het volgende:

```php
PHP Fatal error: Call to undefined method Magento\Catalog\Model\Resource\Product\Interceptor::getWriteConnection() in /var/www/magento2/app/code/Magento/SampleData/Module/Catalog/Setup/Product/Gallery.php on line 144
```

### Oplossing

Schakel tijdens de installatie van voorbeeldgegevens SELinux uit met behulp van een bron zoals:

* [www.ibm.com](https://www.ibm.com/docs/ja/ahts/4.0?topic=t-disabling-selinux)
* [CentOS-documentatie](https://docs.centos.org/en-US/docs/)

## Symptom (vertakking ontwikkelen)

Andere fouten worden weergegeven, zoals:

```php
[Magento\Setup\SampleDataException] Error during sample data installation: Class Magento\Sales\Model\Service\OrderFactory does not exist
```

### Oplossing

Er zijn bekende problemen met het gebruik van voorbeeldgegevens bij de Adobe Commerce Developer Branch. Gebruik in plaats hiervan de hoofdvertakking. U kunt als volgt naar de hoofdvertakking schakelen:

```php
cd <magento_root>
git checkout master
git pull origin master
```

## Symptoom (max_execute_time)

De installatie wordt gestopt voordat de installatie van de voorbeeldgegevens is voltooid. Hier volgt een voorbeeld:

```php
(more)

Module 'Magento_CustomerSampleData':
Installing data...
```

Installatie van voorbeeldgegevens is niet voltooid.

Deze fout treedt op wanneer de maximale geconfigureerde uitvoertijd van uw PHP scripts wordt overschreden. Omdat het laden van voorbeeldgegevens veel tijd in beslag kan nemen, kunt u de waarde tijdens de installatie verhogen.

### Oplossing

Als gebruiker met `root` rechten, wijzigen `php.ini` om de waarde van `max_execution_time` tot 600 of meer. (600 seconden is 10 minuten. U kunt de waarde naar wens verhogen.) U moet het volgende wijzigen `max_execution_time` terug naar de vorige waarde nadat de installatie is gelukt.

Als u niet zeker bent waar `php.ini` bevindt, voert u de volgende opdracht in:

```php
php --ini
```

De waarde van `Loaded Configuration File` is de `php.ini` u moet wijzigen.

>[!NOTE]
>
>We zijn ons ervan bewust dat dit artikel wellicht nog steeds standaardsoftwaretermen bevat die sommigen racistisch, seksistisch of onderdrukkend vinden en die de lezer kunnen doen voelen gekwetst, getraumatiseerd of onwelkom. Adobe werkt eraan deze termen te verwijderen uit onze code, documentatie en gebruikerservaring.
