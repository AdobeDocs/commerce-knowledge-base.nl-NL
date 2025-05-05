---
title: Implementatie mislukt met de juiste toegangssleutels in env:COMPOSER_AUTH of auth.json
description: Dit artikel biedt een oplossing voor het probleem wanneer de implementatie mislukt met de fout "Het bestand https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip kan niet worden gedownload (HTTP/1.1 404 niet gevonden)".
feature: Deploy
role: Admin
exl-id: a18f4213-7381-4001-a5a0-3f8db4525469
source-git-commit: 2a1c97c65282d03010bffabbcd2d1be7fb9ff9a6
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Implementatie mislukt met de juiste toegangssleutels in env:COMPOSER_AUTH of auth.json

Dit artikel verstrekt een oplossing voor de kwestie wanneer uw plaatsing met een fout zoals hieronder ontbreekt, in het [ plaatsingslogboek ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log):

```
W:   [Composer\Downloader\TransportException]
W:   The "https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip" file could not be downloaded (HTTP/1.1 404 Not Found)
```

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur 2.4.x

## Probleem

<u> Stappen om </u> te reproduceren:

Poging om te implementeren.

<u> Verwachte resultaten </u>:

De implementatie is voltooid.

<u> Ware resultaten </u>:

>[!NOTE]
>
>Dit is een voorbeeldfout. Er kan een fout optreden die een ander bestand aangeeft (afhankelijk van de Adobe Commerce-versie die u implementeert).

U kunt niet correct implementeren. U ziet een fout als *het &quot;https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip&quot;dossier niet kon worden gedownload (HTTP/1.1 404 niet Gevonden)* in het [ plaatsingslogboek ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

### Oorzaak

De opgegeven toegangstoetsen voor composers die op een van deze locaties worden gevonden, hebben mogelijk geen toegang tot de code:

* in de `env:COMPOSER_AUTH` -variabele op projectniveau
* in de `auth.json file` , die voorrang heeft op de `env:COMPOSER_AUTH` -variabele.

### Oplossing

Werk `env:COMPOSER_AUTH` variabele op het projectniveau bij en zorg ervoor dat het met sleutels wordt gevormd die toegang tot de code hebben.

Voor stappen, verwijs naar [ Variabele niveaus ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure/env/variable-levels) in Commerce op de Gids van de Infrastructuur van de Wolk.

## Gerelateerde lezing

* [Adobe Commerce on cloud repo kan niet worden geopend: 403 Verboden of 404 Geen fout gevonden bij implementatie](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html)
* [Implementatiefout: fout 7 tijdens het downloaden ... poort 443: verbinding geweigerd](/help/troubleshooting/deployment/deployment-error-downloading-connection-refused-adobe-commerce.md)
