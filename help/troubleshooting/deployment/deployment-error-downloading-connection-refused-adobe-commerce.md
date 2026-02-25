---
title: 'Implementatiefout: *fout 7 tijdens het downloaden.. poort 443: verbinding geweigerd*'
description: 'Dit artikel biedt een oplossing voor de implementatiefout: *"error 7 while downloading ... port 443: Connection weigerde"*.'
exl-id: 520cf50f-3682-441d-87a7-8e05301a2b0c
feature: Cache, Deploy
role: Developer
source-git-commit: c005409900021a72d73c10a2df5f23be3f2bc2cf
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# De fout van de plaatsing: *fout 7 terwijl het downloaden... haven 443: Verbinding weigerde*

Dit artikel biedt een oplossing voor het probleem wanneer de implementatie mislukt met het volgende foutbericht:

```bash
W: In CurlDownloader.php line 370:
W:
W:   curl error 7 while downloading https://repo.packagist.org/p2/magento/module
W:   -sitemap.json: Failed to connect to repo.packagist.org port 443: Connection
W:    refused
```

## Betrokken versies

Adobe Commerce op wolkeninfrastructuur, [ alle gesteunde versies ](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Probleem

De plaatsing ontbreekt met a **krulfout 7** bericht.

<u> Stappen om </u> te reproduceren:

Trigger een plaatsing.

<u> Verwacht gedrag </u>:

Implementatie is geslaagd.

<u> Ware gedrag </u>:

De plaatsing ontbreekt, en de volgende fout: *curl fout 7 terwijl het downloaden.. haven 443: Verweigerde Verbinding* verschijnt in opstellen logboek.

## Oorzaak

Dit kan gebeuren als de cacheverbinding met de repo verloren gaat.

## Oplossing

Vraag een Super Gebruiker op het project om dit bevel in werking te stellen:

```bash
magento-cloud project:clear-build-cache -p <project ID>
```

Om te controleren wie op het project een Super Gebruiker is, verwijs naar [ Mening de het projectrol van een gebruiker ](/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=en#view-a-user’s-project-role) in Commerce op de Gids van de Infrastructuur van de Wolk.

## Aanbevolen lezen

* [ de plaatsingsproblemen van Adobe Commerce ](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-29640).
* [ Adobe Commerce op wolkenrepo kon niet worden betreden: 403 Verboden of 404 niet Gevonden fout toen het opstellen van ](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html).
* [ de Plaatsing ontbreekt met &quot;Fout bouwend project: De bouwstijlhaak ontbrak met statuscode 1&quot;](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-fails-with-error-building-project-the-build-hook-failed-with-status-code-1.html).
