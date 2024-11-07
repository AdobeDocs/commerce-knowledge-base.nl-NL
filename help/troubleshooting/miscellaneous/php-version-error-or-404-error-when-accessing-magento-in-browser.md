---
title: PHP-versiefout of 404-fout bij toegang tot Adobe Commerce in browser
description: Dit artikel biedt oplossingen voor de problemen waarbij u geen toegang hebt tot uw Adobe Commerce-exemplaar in een webbrowser en waarvoor een fout van 404 of een "niet-ondersteunde PHP-versie" optreedt.
exl-id: 6cfdeaae-5e52-411c-9006-5af8a467873a
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# PHP-versiefout of 404-fout bij toegang tot Adobe Commerce in browser

Dit artikel biedt oplossingen voor de problemen waarbij u geen toegang hebt tot uw Adobe Commerce-exemplaar in een webbrowser en waarvoor een fout van 404 of een &quot;niet-ondersteunde PHP-versie&quot; optreedt.

## Betrokken producten en versies:

* Adobe Commerce 2.3.x

## Probleem: niet-ondersteunde PHP-versie

Het volgende bericht wordt weergegeven wanneer u toegang probeert te krijgen tot Adobe Commerce Store of Commerce Admin:

`Magento supports PHP 7.1.3 or later. Please read Magento System Requirements.`

### Oplossing

Probeer het volgende:

* Upgrade PHP naar versie 7.3. Voor meer informatie zie [ Adobe Commerce 2.3 de vereisten van de technologiestapel ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements) in onze ontwikkelaarsdocumentatie.
* Start Apache opnieuw, omdat deze mogelijk niet dezelfde PHP-versie gebruikt als op het bestandssysteem. Gebruik de volgende opdrachten om Apache opnieuw te starten:
   * Ubuntu: `service apache2 restart`
   * CentOS: `service httpd restart`

## Probleem: fout 404

Er wordt een fout van 404 (Niet gevonden) weergegeven wanneer u toegang probeert te krijgen tot Adobe Commerce storefront of Commerce Admin.

### Oplossing

Probeer het volgende:

* Zorg ervoor [ de server van Apache herschrijft ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/web-server/apache) wordt toegelaten. Als herschrijvingen van Apache-servers onjuist zijn ingesteld, worden statische bestanden niet op de juiste locatie aangeboden.
* Er kan een probleem zijn met de basis-URL die u tijdens de installatie hebt ingevoerd. U specificeert basis URL als waarde van `--base-url=` wanneer het installeren van Adobe Commerce van de bevellijn of als waarde van het **Uw gebied van het Adres van de Opslag** op de pagina van de Configuratie van het Web van het Webinstallatieprogramma. De basis URL *moet* met de regeling (zoals `http://`) beginnen en met een het slepen schuine streep (/) beëindigen. Voer het installatieprogramma opnieuw uit met een geldige waarde en probeer Adobe Commerce later te openen.
