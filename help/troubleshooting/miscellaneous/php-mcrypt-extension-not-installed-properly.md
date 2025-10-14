---
title: PHP-coderingsextensie is niet correct geïnstalleerd
description: PHP-coderingsextensie is niet correct geïnstalleerd
exl-id: 1010349e-6631-4a05-8883-5cc903d67534
feature: Extensions, Install
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# PHP-coderingsextensie is niet correct geïnstalleerd

>[!WARNING]
>
>GELIEVE NOTA TE NEMEN: De crypt bibliotheekeigenschap was [&#x200B; afgekeurd van PHP 7.1 en werd verwijderd uit PHP 7.2 &#x200B;](https://www.php.net/manual/en/intro.mcrypt.php).

## Detail

Fouten kunnen het volgende omvatten:

```php
exception 'Exception' with message 'PHP Warning: PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory
```

```php
Installing data fixtures:
/usr/bin/php -f '/Users/username/www/magento/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/Users/username/www/magento' 2>&1
[ERROR] exception 'Exception' with message '
Fatal error: Uncaught exception 'Exception' with message 'Module 'Magento_Core' depends on 'mcrypt' PHP [extension](https://experienceleague.adobe.com/nl/docs/commerce-operations/operational-playbook/glossary#extension) that is not loaded.'
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

* Opstelling a {[&#128279;](http://kb.mediatemple.net/questions/764/How+can+I+create+a+phpinfo.php+page%3F#gs) dossier 0} phpinfo.php in de wortelfolder van de Webserver en onderzoek de output in Webbrowser.
* Voer de volgende opdracht uit:    `$ php -r "phpinfo();" | grep mcrypt`

Als crypt *niet* geïnstalleerd is, berichten gelijkend op de volgende vertoning:

```php
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
```

In sommige gevallen, zou u de software van Adobe Commerce van de [&#x200B; bevellijn &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/advanced) kunnen moeten installeren en de volledige weg aan de stapel specificeren van de LAMP die geïnstalleerde crypt heeft.
