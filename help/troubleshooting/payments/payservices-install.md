---
title: Installeren van betalingsservices problemen oplossen
description: In dit artikel worden de fouten uitgelegd die u kunt ervaren tijdens de installatie van Betalingsservices. Ook worden oplossingen geboden voor het verhelpen van deze fouten, zodat u de installatie kunt voltooien.
exl-id: 0aef7482-8834-400e-85b9-d3d3eb0ab76e
feature: Install, Orders, Payments, Saas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# Installeren van betalingsservices problemen oplossen

In dit artikel worden de fouten uitgelegd die u kunt ervaren tijdens de installatie van Betalingsservices. Ook worden oplossingen geboden voor het verhelpen van deze fouten, zodat u de installatie kunt voltooien.

## Betrokken producten en versies

* [Betalingsdiensten](https://marketplace.magento.com/magento-payment-services.html) is nu compatibel met Adobe Commerce-versies 2.4.0 tot en met 2.4.4.

## Probleem - onjuiste composer-sleutels

Wanneer u de extensie Betalingsservices installeert, wordt mogelijk een foutbericht weergegeven met de mededeling dat u tijdens de installatie onjuiste Composer-sleutels hebt gebruikt.

<u>Stappen om te reproduceren</u>:

1. Poging tot [Betalingsservices installeren](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html).
1. Zie de volgende fout:

   *Kan geen overeenkomende versie van pakketmagento/betalingsservices vinden. Controleer de spelling van het pakket, de versiebeperking en of het pakket beschikbaar is in een stabiliteit die overeenkomt met de minimale stabiliteit (stabiel).*

<u>Verwacht resultaat</u>:

U kunt deze [installatie-instructies](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) in onze ontwikkelaarsdocumentatie om de Betalingsdiensten met succes te installeren.

<u>Werkelijk resultaat</u>:

Tijdens de installatie wordt een foutbericht weergegeven dat u tijdens de installatie niet de juiste Composer-toetsen hebt gebruikt.

### Oorzaak

Tijdens de installatie hebt u onjuiste Composer-toetsen gebruikt.

### Oplossing

Controleren of [uw Composer-sleutels zijn gekoppeld aan de Magento-id](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html#incorrect-composer-keys) gebruikt tijdens de registratie van betalingsservices.

## Probleem - het gebruiken van zelfde gegevensruimte over veelvoudige instanties

Het runnen van een multi-milieu opstelling met de Diensten van de Betaling op elk.

### Oplossing

Dezelfde API-sleutel kan voor alle instanties worden gebruikt, maar elke instantie moet zijn eigen SaaS-gegevensruimte gebruiken.

Wanneer u een SaaS-project maakt, genereert Commerce een of meer SaaS-gegevensruimten, afhankelijk van uw Commerce-licentie:

* Adobe Commerce - Eén productiedeswitruimte; twee testgegevensruimten
* Magento Open Source - Eén gegevensruimte voor productie; geen gegevensruimten voor tests

Instructies volgen in [Commerce API-sleutel en persoonlijke sleutel](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#obtain-api-credentials) om uw uitbreiding van de Betalingsdiensten met succes te vormen.

## Probleem - onvoldoende geheugen voor PHP

Wanneer u de extensie Betalingsservices installeert, wordt mogelijk een foutbericht weergegeven dat u onvoldoende geheugen hebt voor PHP.

<u>Stappen om te reproduceren</u>:

1. Poging tot [Betalingsservices installeren](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html).
1. Zie de volgende fout, of gelijkaardig:

   *Fatale fout: toegestane geheugengrootte van 2146435072 bytes is uitgeput (geprobeerd 4096 bytes toe te wijzen) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php op regel 52*

<u>Verwacht resultaat</u>:

U kunt deze [installatie-instructies](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) in onze ontwikkelaarsdocumentatie om de Betalingsdiensten met succes te installeren.

<u>Werkelijk resultaat</u>:

Tijdens de installatie wordt een foutbericht weergegeven dat je onvoldoende geheugen hebt voor PHP.

### Oorzaak

De limiet voor PHP op je omgeving is niet ingesteld op een hoog genoeg niveau.

### Oplossing

[De geheugenlimiet voor PHP verhogen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html#not-enough-memory-for-php) over uw omgeving in `php.ini`.
