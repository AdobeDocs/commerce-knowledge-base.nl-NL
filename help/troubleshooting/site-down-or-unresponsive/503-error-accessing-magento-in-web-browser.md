---
title: 503-fout Adobe Commerce openen in webbrowser
description: Dit artikel biedt een mogelijke oplossing voor het probleem waarbij u een fout van 503 krijgt wanneer u probeert toegang te krijgen tot Adobe Commerce storefront en/of Admin.
exl-id: 4232aa21-40c2-41b0-9fb0-fc8cd4db8e39
feature: Storefront
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# 503-fout Adobe Commerce openen in webbrowser

Dit artikel biedt een mogelijke oplossing voor het probleem waarbij u een fout van 503 krijgt wanneer u probeert toegang te krijgen tot Adobe Commerce storefront en/of Admin.

## Betrokken producten en versies

Adobe Commerce 2.3.x

## Probleem {#symptoms}

<u>Stappen om te reproduceren</u>

(Voorwaarden: zorg dat de winkel zich niet bevindt in [onderhoudsmodus](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-mode.html#config-mode-show)).

Navigeer in een webbrowser naar uw Commerce-beheerder of -winkel.

<u>Verwacht resultaat</u>

De pagina wordt geladen.

<u>Werkelijk resultaat</u>

U krijgt HTTP 503 (de Dienst niet beschikbaar) fout. De Apache `error.log` bevat het volgende bericht:

*Ongeldige opdracht &#39;Order&#39;, mogelijk onjuist gespeld of gedefinieerd door een module die niet is opgenomen in de serverconfiguratie.*

## Oorzaak {#details}

Compatibiliteitsmodule Apache 2.4 `mod_access_compat` is uitgeschakeld, wat ertoe leidt dat Adobe Commerce URL herschrijft niet correct werkt.

## Oplossing {#suggested-solution}

De optie `mod_access_compat` Apache module en start Apache opnieuw door het volgende uit te voeren als een gebruiker met &#39;basisrechten&#39;:

```bash
a2enmod access_compat
service <name> restart
```

Op CentOS,

```bash
<name>
```

is

```bash
httpd
```

. Op Ubuntu

```bash
<name>
```

is

```bash
apache2
```

.

## Gerelateerde lezing {#additional-resources}

* [Apache-documentatie over mod\_access\_compat](https://httpd.apache.org/docs/current/mod/mod_access_compat.html)
* [Apache-documentatie over mod\_authz\_host](https://httpd.apache.org/docs/current/mod/mod_authz_host.html)
* [Volgorde, Toestaan, Weigeren van de Apache Definitive Guide](https://docstore.mik.ua/orelly/linux/apache/ch05_06.htm)
* [askubuntu.com](https://askubuntu.com/questions/335228/changes-in-apache-config-between-12-04-2-and-12-04-3-lts)
