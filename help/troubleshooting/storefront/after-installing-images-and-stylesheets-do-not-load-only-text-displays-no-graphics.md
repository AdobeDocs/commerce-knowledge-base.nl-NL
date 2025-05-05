---
title: Na de installatie worden afbeeldingen en opmaakmodellen niet geladen. Alleen tekstweergaven, geen afbeeldingen
description: In dit artikel worden de mogelijke redenen en oplossingen beschreven voor het probleem waarbij opmaakmodellen en afbeeldingen na de installatie van Adobe Commerce niet worden geladen.
exl-id: f33cee89-b416-4d63-8cc5-9cc57618ce92
feature: Install, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

<u> Stappen om te reproduceren </u>

1. Adobe Commerce installeren.
1. Navigeer naar de storefront of Admin.

<u> Verwacht resultaat </u>

Er worden stijlen toegepast. Geen enkel interface-element ziet er anders uit dan ontbrekende stijlen.

<u> Werkelijk resultaat </u>

Stijlen worden niet correct toegepast, afbeeldingen ontbreken.

## Oorzaak

Het pad naar afbeeldingen en opmaakmodellen is onjuist, omdat de basis-URL onjuist is of omdat serverherschrijvingen (CentOS, Ubuntu) niet juist zijn ingesteld.

Om dit te bevestigen, gebruik Webbrowser inspecteur om de wegen aan statische activa te controleren en te verifiëren dat die activa op het Adobe Commerce of het dossiersysteem van de Magento Open Source worden gevestigd.

Statische elementen bevinden zich onder `<magento_root>/pub/static/` , in de mappen `frontend` en `adminhtml` .

## Oplossing

De volgende oplossingen zijn mogelijke oplossingen afhankelijk van de software u gebruikt en de oorzaak van het probleem:

* Als u de Apache Webserver gebruikt, verifieer uw [ server herschrijft ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/prerequisites/web-server/apache#apache-rewrites-and-htaccess) het plaatsen en de basis URL van uw server Adobe Commerce/Magento Open Source en probeert opnieuw. Als u de aanwijzing Apache `AllowOverride` onjuist instelt, worden de statische bestanden niet op de juiste locatie aangeboden.
* Als u de nginx Webserver gebruikt, ben zeker om een virtueel gastheerdossier [&#128279;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/prerequisites/web-server/nginx) te vormen.  Het virtuele nginx-hostbestand moet aan de volgende criteria voldoen:
   * De instructie `include` moet verwijzen naar het voorbeeldconfiguratiebestand nginx in de installatiemap van Adobe Commerce/Magento Open Source. Bijvoorbeeld:    `include /var/www/html/magento2/nginx.conf.sample;`
   * De aanwijzing `server_name` moet overeenkomen met de basis-URL die u hebt opgegeven bij de installatie van Adobe Commerce/Magento Open Source. Bijvoorbeeld: `server_name 192.186.33.10;`
* Als de toepassing op [ productiemodus ](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/setup/application-modes#production-mode) is, probeer plaatsend statische meningsdossiers gebruikend het `magento setup:static-content:deploy` bevel. Voor details over het opstellen van statische dossiers verwijzen naar [ Statische meningsdossiers ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) in onze ontwikkelaarsdocumentatie opstellen.
