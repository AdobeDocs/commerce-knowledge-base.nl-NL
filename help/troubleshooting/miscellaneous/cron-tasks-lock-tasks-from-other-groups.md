---
title: Taken uitsnijden vergrendelen taken uit andere groepen
description: Dit artikel biedt een oplossing voor het Adobe Commerce-probleem met de cloudinfrastructuur, dat verband houdt met bepaalde lange-termijntaken voor cron die andere cron-taken blokkeren.
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Taken uitsnijden vergrendelen taken uit andere groepen

Dit artikel biedt een oplossing voor het Adobe Commerce-probleem met de cloudinfrastructuur, dat verband houdt met bepaalde lange-termijntaken voor cron die andere cron-taken blokkeren.

## Betrokken producten en versies

* Adobe Commerce on cloud Infrastructure Pro-planarchitectuur
* Aan boord vóór mei 2019

## Probleem

In Adobe Commerce for Cloud kunnen andere uitvoeringstaken worden vergrendeld wanneer u complexe uitsnijdtaken hebt (taken op lange termijn). De taak van indexeerders herstelt bijvoorbeeld de ongeldig gemaakte indexen. Het kan een paar uur duren om te voltooien en het zal andere standaardtaken vergrendelen, zoals het verzenden van e-mails, het genereren van sitemaps, klantmeldingen en andere aangepaste taken.

<u>Symptomen</u>:

De processen die worden uitgevoerd door snijtaken worden niet uitgevoerd. Productupdates worden bijvoorbeeld niet gedurende uren toegepast of klanten melden geen e-mails te ontvangen.

Wanneer u het dialoogvenster `cron_schedule` databasetabel, u ziet de taken met `missed` status.

## Oorzaak

Eerder, in onze wolkenomgeving, werd de server Jenkins gebruikt om bouwbanen in werking te stellen. Jenkins zal slechts één geval van een baan in een tijd in werking stellen; bijgevolg zal er slechts één zijn `bin/magento cron:run` proces dat tegelijkertijd wordt uitgevoerd.

## Oplossing

1. Contact [Adobe Commerce-ondersteuning](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om zelf-beheerde toe te laten kronnen.
1. Bewerk de `.magento.app.yaml` bestand in de hoofdmap van de code voor Adobe Commerce in de Git-vertakking. Voeg het volgende toe:

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. Sla het bestand op en druk updates naar de omgevingen voor Staging en Productie (net als bij Integratieomgevingen).

>[!NOTE]
>
>Er is geen behoefte om oude kroonconfiguraties over te brengen waar de veelvoudige `cron:run` zijn opgenomen in het nieuwe uitsnijdschema; de normale `cron:run` taak, toegevoegd zoals hierboven beschreven, is genoeg. Het is echter wel verplicht om aangepaste taken over te dragen als u die hebt.

### Controleren of de functie voor zelfbeheerd uitsnijden is ingeschakeld (alleen voor Staging en productie in Cloud Pro)

Als u wilt controleren of de zelfbeheerde uitsnede is ingeschakeld, voert u de opdracht `crontab -l` en observeer het resultaat:

* Zelf-geleid kruin wordt toegelaten, als u de taken, als het volgende kunt zien:

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* De zelfbeheerde uitsnede wordt niet ingeschakeld als u de taken niet kunt zien en de *&quot;U mag dit programma niet gebruiken&quot;* foutbericht.

>[!NOTE]
>
>Het hierboven vermelde bevel om te controleren of wordt de zelf-beheerde kroon toegelaten is niet op een Plan van de Aanzet en in het ontwikkelings/integratiemilieu van toepassing.

## Gerelateerde lezing

* [Uitsnijdtaken instellen](https://devdocs.magento.com/guides/v2.3/cloud/configure/setup-cron-jobs.html) in onze documentatie voor ontwikkelaars
