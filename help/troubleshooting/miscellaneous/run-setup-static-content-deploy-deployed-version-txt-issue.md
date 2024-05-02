---
title: '"setup uitvoeren:static-content:Implementeer het probleem "distribueren_version.txt"'
description: Dit artikel verstrekt een moeilijke situatie voor ` opstellen_version.txt ` is geen beschrijfbare fout wanneer het runnen van ` opstelling:static-content:implementeren.
exl-id: 88d8c126-349f-49cd-8f02-2a32e4994521
feature: Deploy, Page Content, SCD
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# run `setup:static-content:deploy` issue_version.tx

Dit artikel bevat een oplossing voor `deployed_version.txt` is geen beschrijfbare fout wanneer u het `setup:static-content:deploy` handmatig.

## Probleem

Als u de Adobe Commerce-aanbevelingen voor cloudinfrastructuur opvolgt, kunt u deze gebruiken [Configuratiebeheer](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) (en het genereren van statische elementen verplaatsen naar de constructiefase om de downtime van websites tijdens de implementatie te verminderen), kan de volgende fout optreden wanneer u de `setup:static-content:deploy` handmatig opdracht:

```
{{cloud-project-id}}_stg@i:~$ php bin/magento setup:static-content:deploy
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/luma, Aheadworks/marketplace, Magento/backend
[Magento\Framework\Exception\FileSystemException]
The path "deployed_version.txt:///app/{{cloud-project-id}}_stg/pub/static/app/{{cloud-project-id}}_stg/pub/static/" is not writable
```

## Oorzaak

We hebben het implementatieproces geoptimaliseerd om de downtime te verminderen en symlinks naar statische bestanden gemaakt in plaats van deze te kopiëren. De locatie waar de statische elementen worden opgeslagen, is alleen-lezen. Daarom wordt het foutbericht hierboven weergegeven.

We raden ten zeerste aan om statische inhoud handmatig te implementeren, omdat alle elementen al zijn gegenereerd en er geen verschil is tussen bestanden als u deze handmatig uitvoert (de themabestanden zijn ook alleen-lezen, u kunt ze niet wijzigen). Een dergelijke bewerking heeft dus geen zin.

## Oplossing

Als u nog statische inhoudsplaatsing wilt in werking stellen, verwijder symlinks in `pub/static` en voert de `setup:static-content:deploy` opnieuw gebruiken:

```
find pub/static/ -maxdepth 1 -type l -delete
```
