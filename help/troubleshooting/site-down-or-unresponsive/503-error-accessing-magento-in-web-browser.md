---
title: 503-fout Adobe Commerce openen in webbrowser
description: Dit artikel biedt een mogelijke oplossing voor het probleem waarbij u een fout van 503 krijgt wanneer u probeert toegang te krijgen tot Adobe Commerce storefront en/of Admin.
exl-id: 4232aa21-40c2-41b0-9fb0-fc8cd4db8e39
feature: Storefront
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# 503-fout Adobe Commerce openen in webbrowser

Dit artikel biedt een mogelijke oplossing voor het probleem waarbij u een fout van 503 krijgt wanneer u probeert toegang te krijgen tot Adobe Commerce storefront en/of Admin.

## Betrokken producten en versies

Adobe Commerce 2.3.x

## Probleem {#symptoms}

<u> Stappen om te reproduceren </u>

(Eerste vereisten: zorg ervoor de opslag niet op [ onderhoudswijze ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/set-mode#config-mode-show) is).

Navigeer in een webbrowser naar uw Commerce-beheerder of -winkel.

<u> Verwacht resultaat </u>

De pagina wordt geladen.

<u> Werkelijk resultaat </u>

U krijgt HTTP 503 (de Dienst niet beschikbaar) fout. Apache `error.log` bevat het volgende bericht:

*Ongeldig bevel &quot;Orde&quot;, misschien verkeerd gespeld of bepaald door een module niet inbegrepen in de serverconfiguratie.*

## Oorzaak {#details}

De compatibiliteitsmodule Apache 2.4 `mod_access_compat` is uitgeschakeld, zodat de URL van Adobe Commerce anders werkt.

## Oplossing {#suggested-solution}

Schakel de Apache-module `mod_access_compat` in en start Apache opnieuw door het volgende uit te voeren als een gebruiker met &#39;basisrechten&#39;:

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

* [ Apache documentatie over mod\_access\_compat ](https://httpd.apache.org/docs/current/mod/mod_access_compat.html)
* [ documentatie Apache over mod\_authz\_host ](https://httpd.apache.org/docs/current/mod/mod_authz_host.html)
* [ orde, sta toe, ontken van de Definitieve Gids van Apache ](https://docstore.mik.ua/orelly/linux/apache/ch05_06.htm)
* [ askubuntu.com ](https://askubuntu.com/questions/335228/changes-in-apache-config-between-12-04-2-and-12-04-3-lts)
