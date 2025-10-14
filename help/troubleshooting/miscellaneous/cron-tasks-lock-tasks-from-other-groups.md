---
title: '[!DNL Cron] taken vergrendelen taken uit andere groepen'
description: Dit artikel verstrekt een oplossing voor Adobe Commerce op de kwestie van de wolkeninfrastructuur met betrekking tot bepaalde lange looppas  [!DNL cron]  banen die andere  [!DNL cron]  banen blokkeren.
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# [!DNL Cron] taken vergrendelen taken uit andere groepen

Dit artikel biedt een oplossing voor het probleem met de cloudinfrastructuur van Adobe Commerce met betrekking tot bepaalde [!DNL cron] -taken op lange termijn die andere [!DNL cron] -taken blokkeren.

## Betrokken producten en versies

* Adobe Commerce on cloud Infrastructure Pro-planarchitectuur
* Aan boord vóór mei 2019

## Probleem

In Adobe Commerce for cloud kunnen complexe [!DNL cron] taken (taken op lange termijn) andere taken vergrendelen. De taak van indexeerders herstelt bijvoorbeeld de ongeldig gemaakte indexen. Het kan een paar uur duren om te voltooien en het zal andere standaardtaken van [!DNL cron] vergrendelen, zoals het verzenden van e-mails, het genereren van sitemaps, klantmeldingen en andere aangepaste taken.

<u> Symptomen </u>:

De processen die worden uitgevoerd door [!DNL cron] -taken worden niet uitgevoerd. Productupdates worden bijvoorbeeld niet gedurende uren toegepast of klanten melden geen e-mails te ontvangen.

Wanneer u de databasetabel `cron_schedule` opent, ziet u de taken met de status `missed` .

## Oorzaak

Eerder, in onze wolkenomgeving, werd de server Jenkins gebruikt om [!DNL cron] banen in werking te stellen. Jenkins voert slechts één instantie van een taak tegelijk uit. Er wordt dus slechts één `bin/magento cron:run` -proces tegelijk uitgevoerd.

## Oplossing

1. De steun van Adobe Commerce van het contact [&#128279;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om zelf-geleid [!DNL crons] toegelaten te hebben.
1. Bewerk het `.magento.app.yaml` -bestand in de hoofdmap van de code voor Adobe Commerce in de [!DNL Git] -vertakking. Voeg het volgende toe:

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. Sla het bestand op en druk updates naar de omgevingen voor Staging en Productie (net als bij Integratieomgevingen).

>[!NOTE]
>
>Het is niet nodig oude [!DNL cron] configuraties over te dragen waarbij meerdere `cron:run` aanwezig zijn in het nieuwe [!DNL cron] -schema. De normale `cron:run` taak, toegevoegd zoals hierboven beschreven, is voldoende. Het is echter wel verplicht om aangepaste taken over te dragen als u die hebt.

### Controleren of u de functie voor zelfbeheer van [!DNL cron] hebt ingeschakeld (alleen voor Staging en productie in Cloud Pro)

Als u wilt controleren of de zelfbeheerde [!DNL cron] is ingeschakeld, voert u de opdracht `crontab -l` uit en bekijkt u het resultaat:

* Self-managed [!DNL cron] is ingeschakeld als u de taken kunt zien, zoals in het volgende voorbeeld:

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* Het zelf-beheerde [!DNL cron] wordt niet toegelaten als u niet de taken kunt zien en *krijgt &quot;u wordt niet toegestaan om dit programma&quot;te gebruiken* foutenmelding.

>[!NOTE]
>
>De bovenstaande opdracht om te controleren of self-managed [!DNL cron] is ingeschakeld, geldt niet voor een Starter-abonnement en in de ontwikkelings-/integratieomgeving.

## Gerelateerde lezing

* [!DNL cron]  de banen van de opstelling [&#128279;](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) in onze ontwikkelaarsdocumentatie
* [&#x200B; Beste praktijken voor het wijzigen van gegevensbestandlijsten &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
