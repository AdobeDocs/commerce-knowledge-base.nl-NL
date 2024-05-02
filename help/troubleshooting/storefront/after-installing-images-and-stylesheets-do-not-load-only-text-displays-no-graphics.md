---
title: Na de installatie worden afbeeldingen en opmaakmodellen niet geladen. Alleen tekstweergaven, geen afbeeldingen
description: In dit artikel worden de mogelijke redenen en oplossingen beschreven voor het probleem waarbij opmaakmodellen en afbeeldingen na de installatie van Adobe Commerce niet worden geladen.
exl-id: f33cee89-b416-4d63-8cc5-9cc57618ce92
feature: Install, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# Na de installatie worden afbeeldingen en opmaakmodellen niet geladen. Alleen tekstweergaven, geen afbeeldingen

In dit artikel worden de mogelijke redenen en oplossingen beschreven voor het probleem waarbij opmaakmodellen en afbeeldingen na de installatie van Adobe Commerce niet worden geladen.

## Betrokken producten en versies

* Adobe Commerce 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Probleem

<u>Stappen om te reproduceren</u>

1. Adobe Commerce installeren.
1. Navigeer naar de storefront of Admin.

<u>Verwacht resultaat</u>

Er worden stijlen toegepast. Geen enkel interface-element ziet er anders uit dan ontbrekende stijlen.

<u>Werkelijk resultaat</u>

Stijlen worden niet correct toegepast, afbeeldingen ontbreken.

## Oorzaak

Het pad naar afbeeldingen en opmaakmodellen is onjuist, omdat de basis-URL onjuist is of omdat serverherschrijvingen (CentOS, Ubuntu) niet juist zijn ingesteld.

Om dit te bevestigen, gebruik Webbrowser inspecteur om de wegen aan statische activa te controleren en te verifiëren dat die activa op het Adobe Commerce of het dossiersysteem van de Magento Open Source worden gevestigd.

Statische elementen bevinden zich onder `<magento_root>/pub/static/` binnen de `frontend` en `adminhtml` mappen.

## Oplossing

De volgende oplossingen zijn mogelijke oplossingen afhankelijk van de software u gebruikt en de oorzaak van het probleem:

* Als u de Apache-webserver gebruikt, moet u uw [server herschrijft](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/apache.html#apache-help-rewrite) en de basis-URL van uw Adobe Commerce/Magento Open Source-server instellen en het opnieuw proberen. Als u Apache instelt `AllowOverride` onjuist, de statische dossiers worden niet gediend van de correcte plaats.
* Als u de nginx-webserver gebruikt, moet u [een virtueel hostbestand configureren](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/nginx.html#configure-nginx-ubuntu). Het virtuele nginx-hostbestand moet aan de volgende criteria voldoen:
   * De `include` instructie moet verwijzen naar het voorbeeld-nginx-configuratiebestand in de installatiemap van Adobe Commerce/Magento Open Source. Bijvoorbeeld:    `include /var/www/html/magento2/nginx.conf.sample;`
   * De `server_name` compileraanwijzing moet overeenkomen met de basis-URL die u hebt opgegeven bij de installatie van Adobe Commerce/Magento Open Source. Bijvoorbeeld: `server_name 192.186.33.10;`
* Als de toepassing zich in [productiemodus](https://devdocs.magento.com/guides/v2.3/config-guide/bootstrap/magento-modes.html#production-mode), probeer plaatsend statische meningsdossiers gebruikend `magento setup:static-content:deploy` gebruiken. Zie voor meer informatie over het implementeren van statische bestanden [Statische weergavebestanden gebruiken](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-maint.html) in onze ontwikkelaarsdocumentatie.
