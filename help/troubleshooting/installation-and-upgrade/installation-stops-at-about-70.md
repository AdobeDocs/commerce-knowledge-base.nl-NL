---
title: Installatie stopt bij ongeveer 70%
description: Dit artikel biedt een oplossing voor het geval de installatie bij ongeveer 70% wordt gestopt.
exl-id: 04aa3572-3c42-4565-9f7f-b4d90df96df2
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

* De instelling PHP voor [`max_execution_time` ](http://php.net/manual/en/info.configuration.php#ini.max-execution-time)
* Tijdlijnwaarden voor nginx en Varnish

## Oplossing:

Stel alle volgende opties naar wens in.

### Alle webservers en Varnish {#all-web-servers-and-varnish}

1. Zoek uw `php.ini` gebruikend een [`phpinfo.php` ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software) dossier.
1. Als gebruiker met `root` rechten, opent u `php.ini` in een teksteditor.
1. Zoek de instelling `max_execution_time` .
1. Wijzig de waarde in `18000` .
1. Sla de wijzigingen in `php.ini` op en sluit de teksteditor af.
1. Apache opnieuw starten:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

   Als u nginx of Varnish gebruikt, ga dan verder met de volgende secties.

### alleen nginx {#nginx-only}

Als u nginx gebruikt, gebruikt u de meegeleverde `nginx.conf.sample` instellingen of voegt u als volgt een time-outinstellingen in het configuratiebestand van de nginx-host toe aan de sectie `location ~ ^/setup/index.php` :

```php
location ~ ^/setup/index.php {
    .....................
    fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
}
```

Opnieuw starten, nginx: `service nginx restart`

### Alleen vernis {#varnish-only}

Als u Varnish gebruikt, bewerkt u `default.vcl` en voegt u als volgt een time-outgrenswaarde toe aan de `backend` stanza:

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
