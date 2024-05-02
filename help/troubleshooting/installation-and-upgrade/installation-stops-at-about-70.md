---
title: Installatie stopt bij ongeveer 70%
description: Dit artikel biedt een oplossing voor het geval de installatie bij ongeveer 70% wordt gestopt.
exl-id: 04aa3572-3c42-4565-9f7f-b4d90df96df2
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Installatie stopt bij ongeveer 70%

Dit artikel biedt een oplossing voor het geval de installatie bij ongeveer 70% wordt gestopt.

## Probleem

Tijdens installatie die de Tovenaar van de Opstelling gebruikt, houdt het proces bij ongeveer 70% (met of zonder steekproefgegevens) tegen. Er worden geen fouten weergegeven op het scherm.

## Oorzaak

Veelvoorkomende oorzaken van dit probleem zijn:

* De PHP-instelling voor [`max_execution_time`](http://php.net/manual/en/info.configuration.php#ini.max-execution-time)
* Tijdlijnwaarden voor nginx en Varnish

## Oplossing:

Stel alle volgende opties naar wens in.

### Alle webservers en Varnish {#all-web-servers-and-varnish}

1. Zoek uw `php.ini` met een [`phpinfo.php`](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo) bestand.
1. Als gebruiker met `root` rechten, openen `php.ini` in een teksteditor.
1. Zoek de `max_execution_time` instellen.
1. De waarde wijzigen in `18000` .
1. Sla uw wijzigingen op in `php.ini` en sluit de teksteditor af.
1. Apache opnieuw starten:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

   Als u nginx of Varnish gebruikt, ga dan verder met de volgende secties.

### alleen nginx {#nginx-only}

Als u nginx gebruikt, gebruik dan de meegeleverde code `nginx.conf.sample` of voeg een onderbrekingsmontages in het nginx dossier van de gastheerconfiguratie aan het `location ~ ^/setup/index.php` als volgt:

```php
location ~ ^/setup/index.php {
    .....................
    fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
}
```

Nginx opnieuw starten: `service nginx restart`

### Alleen vernis {#varnish-only}

Als u Varnish gebruikt, bewerkt u `default.vcl` en voeg een time-outgrenswaarde toe aan de `backend` stanza, als hieronder:

```php
backend default {
.....................
      .first_byte_timeout = 600s;
}
```

Start Varnish opnieuw.

```php
service varnish restart
```
