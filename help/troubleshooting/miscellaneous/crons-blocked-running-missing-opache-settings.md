---
title: De einden van het uitsnijden toe te schrijven aan misconfigured of ontbrekende  [!DNL OpCache]  montages
description: Dit artikel verstrekt een oplossing voor wanneer de kringen ophouden werkend toe te schrijven aan misconfigured of ontbrekende  [!DNL OpCache]  montages.
exl-id: 30643ea9-969f-41c8-8e62-b24e56d690cf
feature: Cache
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Uitsnijden gestopt vanwege onjuist geconfigureerde of ontbrekende [!DNL OpCache] instellingen

Dit artikel biedt een oplossing voor het geval dat de uitsnede stopt met werken vanwege ontbrekende of onjuist geconfigureerde [!DNL OpCache] -instellingen.

## Betrokken producten en versies

Adobe Commerce op wolkeninfrastructuur, [&#x200B; alle gesteunde versies &#x200B;](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Probleem

De kroon werkte niet meer.

## Oorzaak

De module [!DNL OpCache] is bijgewerkt naar een nieuwere versie die een [!DNL GraphQL] -plug-in introduceert die de `env.php` in runtime herschrijft en de instelling voor uitsnijden kan overschrijven, wat de uitgave kan hebben veroorzaakt. De [!DNL OpCache] configuratie moet worden bijgewerkt om om het even welke kwesties met `env.php file` te vermijden, en dat werd opgelost in [&#x200B; versie 2002.1.13 &#x200B;](/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package.html?lang=en#v2002.1.13) van het [!DNL ECE Tools] pakket.

## Oplossing

Optie 1: voer het volgende uit in het opdrachtregelgereedschap:

```bash
bin/magento cron:run
```

Een bericht zou kunnen tonen dat de kruin gehandicapt is.

Optie 2: Open het `app/etc/env.php` -bestand - als u het onderstaande ziet, is de uitsnede handmatig uitgeschakeld, is de uitsnede niet opnieuw ingeschakeld vanwege een mislukte implementatie of heeft het probleem te maken met de [!DNL OpCache] -instellingen.

```php
  'cron' =>
  array (
    'enabled' => 0,
  ),
```

1. Als de uitsnede is uitgeschakeld, voert u deze opdracht uit om de uitsnede opnieuw in te schakelen: `vendor/bin/ece-tools cron:enable`
1. Zorg ervoor dat u de nieuwste versie van [!DNL ECE Tools] gebruikt. Als u dat niet doet, voert u een upgrade uit (of gaat u verder met item 3). Voer deze opdracht uit om uw bestaande versie te controleren:
   `composer show magento/ece-tools`
1. Controleer of het `op-exclude.txt` -bestand aanwezig is als de nieuwste versie van [!DNL ECE Tools] al beschikbaar is. Voer hiertoe de volgende opdracht uit:
   `ls op-exclude.txt`.
Als dit bestand niet aanwezig is, voegt u https://github.com/magento/magento-cloud/blob/master/op-exclude.txt toe aan uw repo en past u de wijziging toe en herstelt u deze.
1. U hoeft [!DNL ECE Tools] niet te upgraden, maar u kunt ook gewoon https://github.com/magento/magento-cloud/blob/master/op-exclude.txt toevoegen of wijzigen in uw repo, en vervolgens de wijziging doorvoeren en opnieuw implementeren.

## Gerelateerde lezing

* [Problemen met gereedheid voor uitsnijden](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues.html)
* [Crons, eigenschap](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html)
* [Cron job zit vast in status &quot;running&quot;](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
