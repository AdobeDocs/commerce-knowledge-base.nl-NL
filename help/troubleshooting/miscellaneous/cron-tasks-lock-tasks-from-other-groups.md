---
title: Taken uitsnijden vergrendelen taken uit andere groepen
description: Dit artikel biedt een oplossing voor het Adobe Commerce-probleem met de cloudinfrastructuur, dat verband houdt met bepaalde lange-termijntaken voor cron die andere cron-taken blokkeren.
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: faa80e8233438fc15781341b3a9d5325269d6d20
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

<u> Symptomen </u>:

De processen die worden uitgevoerd door snijtaken worden niet uitgevoerd. Productupdates worden bijvoorbeeld niet gedurende uren toegepast of klanten melden geen e-mails te ontvangen.

Wanneer u de databasetabel `cron_schedule` opent, ziet u de taken met de status `missed` .

## Oorzaak

Eerder, in onze wolkenomgeving, werd de server Jenkins gebruikt om bouwbanen in werking te stellen. Jenkins voert slechts één instantie van een taak tegelijk uit. Er wordt dus slechts één `bin/magento cron:run` -proces tegelijk uitgevoerd.

## Oplossing

1. De steun van Adobe Commerce van het contact ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om zelf-geleide toegelaten kronen te hebben.[
1. Bewerk het `.magento.app.yaml` -bestand in de hoofdmap van de code voor Adobe Commerce in de Git-vertakking. Voeg het volgende toe:

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. Sla het bestand op en druk updates naar de omgevingen voor Staging en Productie (net als bij Integratieomgevingen).

>[!NOTE]
>
>Het is niet nodig om oude uitsnijdconfiguraties over te dragen waarbij meerdere `cron:run` aanwezig zijn in het nieuwe uitsnijdschema. De normale `cron:run` -taak, toegevoegd zoals hierboven beschreven, is voldoende. Het is echter wel verplicht om aangepaste taken over te dragen als u die hebt.

### Controleren of de functie voor zelfbeheerd uitsnijden is ingeschakeld (alleen voor Staging en productie in Cloud Pro)

Als u wilt controleren of de zelfbeheerde uitsnede is ingeschakeld, voert u de opdracht `crontab -l` uit en bekijkt u het resultaat:

* Zelf-geleid kruin wordt toegelaten, als u de taken, als het volgende kunt zien:

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* De zelf-beheerde krong wordt niet toegelaten als u niet de taken kunt zien en *&quot;krijgt u niet toegestaan om dit programma&quot;te gebruiken* foutenmelding.

>[!NOTE]
>
>Het hierboven vermelde bevel om te controleren of wordt de zelf-beheerde kroon toegelaten is niet op een Plan van de Aanzet en in het ontwikkelings/integratiemilieu van toepassing.

## Gerelateerde lezing

* [ de banen van de opstelling cron ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) in onze ontwikkelaarsdocumentatie.
