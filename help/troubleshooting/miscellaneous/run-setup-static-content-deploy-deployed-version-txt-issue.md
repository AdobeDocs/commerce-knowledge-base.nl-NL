---
title: 'looppas "opstelling :static-content: stelt van ` in werking opgestelde_version.txt kwestie'
description: 'Dit artikel verstrekt een moeilijke situatie "opstellen_version.txt"is geen beschrijfbare fout wanneer het in werking stellen van het "opstelling :static-content: stelt"bevel manueel op.'
exl-id: 88d8c126-349f-49cd-8f02-2a32e4994521
feature: Deploy, Page Content, SCD
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# run `setup:static-content:deploy` distributieprobleem_version.txt

Dit artikel bevat een correctie voor `deployed_version.txt` . Dit is geen beschrijfbare fout wanneer u de opdracht `setup:static-content:deploy` handmatig uitvoert.

## Probleem

Als u Adobe Commerce op de aanbevelingen van de wolkeninfrastructuur volgt om [ Beheer van de Configuratie ](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) te gebruiken (en statische activa te bewegen produceren aan het bouwstijlstadium om website onderbreking tijdens plaatsing te verminderen), kunt u de volgende fout zien wanneer het in werking stellen van het `setup:static-content:deploy` bevel manueel:

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

Als u de implementatie van statische inhoud nog steeds wilt uitvoeren, verwijdert u symlinks in de map `pub/static` en voert u de opdracht `setup:static-content:deploy` opnieuw uit:

```
find pub/static/ -maxdepth 1 -type l -delete
```
