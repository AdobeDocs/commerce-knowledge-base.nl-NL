---
title: Uitgave van token en Composer-sleutelprocedures
description: Dit artikel biedt oplossingen voor het probleem van mislukte implementaties met betrekking tot Github-tokenfouten die worden veroorzaakt door verouderde Composer-sleutels.
exl-id: 202cb936-f9ba-49ea-bf0a-6e6994d2337a
feature: Identity Management
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Uitgave van token en Composer-sleutelprocedures

Dit artikel biedt oplossingen voor het probleem van mislukte implementaties met betrekking tot Github-tokenfouten die worden veroorzaakt door verouderde Composer-sleutels.

## Betrokken producten en versies

* Adobe Commerce op wolkeninfrastructuur, [ alle gesteunde versies ](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Composer versie 1.10.20 en lager

>[!NOTE]
>
>Handelaren die zich in Adobe Commerce bevinden, moeten contact opnemen met hun hostprovider om te controleren of ze Composer versie 1.10.21 of hoger gebruiken vanwege de wijzigingen in de tokenindeling die door Git zijn aangebracht.

## Probleem

De plaatsingen ontbreken en de plaatsingslogboeken bevatten informatie gelijkend op het volgende:

*Fatale fout: Uncaught UnexpectedValueException: Uw glitb oauth token voor github.com bevat ongeldige karakters: &quot;ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx&quot;in /app/vendor/composer/composer/src/Composer/IO/BaseIO.php:129*

## Oorzaak

Verouderde Composer sleutels veroorzaken de symbolische mislukkingen van Github die in ontbroken plaatsingen resulteren.

## Oplossing

Werk uw Composer-versie bij naar 1.10.22 om het probleem op te lossen:

1. Voer `composer require “composer/composer”:”>1.10.21` uit in uw lokale omgeving.
1. Dit voegt de vereiste voor die Composer-pakketversie toe. Controleer het vergrendelingsbestand - de versie `composer/composer` moet 1.0.22 of hoger zijn.
1. Vastleggen `composer.json` en `composer.lock` en een implementatie uitvoeren.

Als deze methode niet werkt, gelieve [ een steunkaartje ](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) voor te leggen.

## Gerelateerde lezing

* [ Github Blog: Achter de nieuwe formaten van het authentificatietoken van GitHub ](https://github.blog/2021-04-05-behind-githubs-new-authentication-token-formats/)
* [ InfoQ.com nieuwsartikel: De Veranderingen van GitHub Symbolische Formaat om Identifiability, Geheime Scanning, en Entropy te verbeteren ](https://www.infoq.com/news/2021/04/github-new-token-format/)
