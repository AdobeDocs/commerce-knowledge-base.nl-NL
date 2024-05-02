---
title: PHP-coderingsextensie is niet correct geïnstalleerd
description: PHP-coderingsextensie is niet correct geïnstalleerd
exl-id: 1010349e-6631-4a05-8883-5cc903d67534
feature: Extensions, Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# PHP-coderingsextensie is niet correct geïnstalleerd

>[!WARNING]
>
>OPMERKING: de functie voor de cryptbibliotheek was [vervangen uit PHP 7.1 en verwijderd uit PHP 7.2](https://www.php.net/manual/en/intro.mcrypt.php).

## Detail

Fouten kunnen het volgende omvatten:

```php
exception 'Exception' with message 'PHP Warning: [PHP](https://glossary.magento.com/php) Startup: Unable to load dynamic [library](https://glossary.magento.com/library) '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory
```

```php
Installing data fixtures:
/usr/bin/php -f '/Users/username/www/magento/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/Users/username/www/magento' 2>&1
[ERROR] [exception](https://glossary.magento.com/exception) 'Exception' with message '
Fatal error: Uncaught exception 'Exception' with message 'Module 'Magento_Core' depends on 'mcrypt' PHP [extension](https://glossary.magento.com/extension) that is not loaded.'
```

```php
======================================================================
   The application has thrown an exception!
======================================================================
 Magento\Framework\Exception
 Command returned non-zero exit code:
`/usr/bin/php5 -f '/var/www/magento2/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/var/www/magento2' 2>&1`
```

## Beschrijving

Met name op ontwikkelaarssystemen die een Linux/Apache/MySQL/PHP (LAMP) &quot;stapel&quot;omvatten die van het werkende systeem afzonderlijk is, is het mogelijk dat crypt of niet bij allen geïnstalleerd of in de weg van de stapel van LAMP maar niet de weg van het werkende systeem is geïnstalleerd.

Als gevolg hiervan kan het Adobe Commerce-installatieprogramma de extensie niet vinden en mislukt de installatie.

## Suggestie

Bepaal of de cryptextensie op een van de volgende manieren is geladen:

* Een [phpinfo.php](http://kb.mediatemple.net/questions/764/How+can+I+create+a+phpinfo.php+page%3F#gs) in de hoofdmap van de webserver en bekijk de uitvoer in een webbrowser.
* Voer de volgende opdracht uit:    `$ php -r "phpinfo();" | grep mcrypt`

Als mcrypt is *niet* geïnstalleerd, berichten gelijkend op de volgende vertoning:

```php
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
```

In sommige gevallen moet u mogelijk de Adobe Commerce-software installeren via de [opdrachtregel](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli.html) en geeft u het volledige pad op naar de LAMP-stapel waarop de crypt is geïnstalleerd.
