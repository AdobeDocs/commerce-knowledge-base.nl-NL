---
title: 'Implementatiefout: *fout 7 tijdens het downloaden.. poort 443: verbinding geweigerd*'
description: 'Dit artikel biedt een oplossing voor de implementatiefout: *"fout 7 tijdens het downloaden van ... poort 443: verbinding geweigerd"*.'
exl-id: 520cf50f-3682-441d-87a7-8e05301a2b0c
feature: Cache, Deploy
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Implementatiefout: *fout 7 tijdens het downloaden ... poort 443: verbinding geweigerd*

Dit artikel biedt een oplossing voor het probleem wanneer de implementatie mislukt met het volgende foutbericht:

```bash
W: In CurlDownloader.php line 370:
W:
W:   curl error 7 while downloading https://repo.packagist.org/p2/magento/module
W:   -sitemap.json: Failed to connect to repo.packagist.org port 443: Connection
W:    refused
```

## Betrokken versies

Adobe Commerce op cloudinfrastructuur, [alle ondersteunde versies](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Probleem

Implementatie mislukt met een **cursiefout 7** bericht.

<u>Stappen om te reproduceren</u>:

Trigger een plaatsing.

<u>Verwacht gedrag</u>:

Implementatie is geslaagd.

<u>Werkelijk gedrag</u>:

Implementatie mislukt en de volgende fout: *fout 7 tijdens het downloaden van ... poort 443: verbinding geweigerd* verschijnt in opstellen logboek.

## Oorzaak

Dit kan gebeuren als de cacheverbinding met de repo verloren gaat.

## Oplossing

Vraag een Super Gebruiker op het project om dit bevel in werking te stellen:

```bash
magento-cloud project:clear-build-cache -p <project ID>
```

Om te controleren wie op het project een SuperGebruiker is, verwijs naar [De projectrol van een gebruiker weergeven](/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=en#view-a-user’s-project-role) in de Commerce on Cloud Infrastructure Guide.

## Aanbevolen lezen

* [Adobe Commerce-probleemoplossing voor implementatie](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter.html).
* [Adobe Commerce on cloud repo kan niet worden geopend: 403 Verboden of 404 Geen fout gevonden bij implementatie](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html).
* [De plaatsing ontbreekt met &quot;Fout bouwend project: De bouwstijlhaak ontbrak met statuscode 1](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-fails-with-error-building-project-the-build-hook-failed-with-status-code-1.html).
