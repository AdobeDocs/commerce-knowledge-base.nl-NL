---
title: Snijstops als gevolg van foutief configureren of ontbreken [!DNL OpCache] instellingen
description: Dit artikel biedt een oplossing voor het geval dat de manschappen niet meer werken als gevolg van foutief geconfigureerde of ontbrekende [!DNL OpCache] instellingen.
exl-id: 30643ea9-969f-41c8-8e62-b24e56d690cf
feature: Cache
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Uitsnijden gestopt als gevolg van onjuist geconfigureerd of ontbreken [!DNL OpCache] instellingen

Dit artikel biedt een oplossing voor wanneer de uitsnede stopt met werken bij ontbrekende of onjuist geconfigureerde [!DNL OpCache] instellingen.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur, [alle ondersteunde versies](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Probleem

De kroon werkte niet meer.

## Oorzaak

De [!DNL OpCache] is bijgewerkt naar een nieuwere versie die een [!DNL GraphQL] insteekmodule waarmee de `env.php` in runtime en kan de instelling voor uitsnijden worden genegeerd. Dit kan het probleem hebben veroorzaakt. De [!DNL OpCache] De configuratie moet worden bijgewerkt om problemen met de `env.php file`en dat is opgelost in [versie 2002.1.13](/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package.html?lang=en#v2002.1.13) van de [!DNL ECE Tools] pakket.

## Oplossing

Optie 1: voer het volgende uit in het opdrachtregelgereedschap:

```bash
bin/magento cron:run
```

Een bericht zou kunnen tonen dat de kruin gehandicapt is.

Optie 2: De optie `app/etc/env.php` bestand - als u het onderstaande ziet, is de uitsnede handmatig uitgeschakeld, is de bewerking niet opnieuw ingeschakeld vanwege een mislukte implementatie of is het probleem gerelateerd aan de [!DNL OpCache] instellingen.

```php
  'cron' =>
  array (
    'enabled' => 0,
  ),
```

1. Als de uitsnede is uitgeschakeld, voert u deze opdracht uit om de uitsnede weer in te schakelen: `vendor/bin/ece-tools cron:enable`
1. Zorg ervoor dat u de nieuwste versie van [!DNL ECE Tools]. Als u dat niet doet, voert u een upgrade uit (of gaat u verder met item 3). Voer deze opdracht uit om uw bestaande versie te controleren:
   `composer show magento/ece-tools`
1. Als u al in de nieuwste versie van [!DNL ECE Tools], controleert u of de `op-exclude.txt` bestand. Voer hiertoe de volgende opdracht uit:
   `ls op-exclude.txt`.
Als dit bestand niet aanwezig is, voegt u https://github.com/magento/magento-cloud/blob/master/op-exclude.txt toe aan uw repo en past u de wijziging toe en herstelt u deze.
1. Zonder upgrade [!DNL ECE Tools], kunt u ook gewoon https://github.com/magento/magento-cloud/blob/master/op-exclude.txt toevoegen/wijzigen in uw repo, vervolgens de wijziging doorvoeren en opnieuw implementeren.

## Gerelateerde lezing

* [Problemen met gereedheid voor uitsnijden](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues.html)
* [Crons, eigenschap](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html)
* [Cron job zit vast in status &quot;running&quot;](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
