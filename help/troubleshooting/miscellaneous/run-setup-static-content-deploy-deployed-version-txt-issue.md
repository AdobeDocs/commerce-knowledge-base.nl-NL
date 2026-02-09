---
title: 'looppas "opstelling :static-content: stelt van ` in werking opgestelde_version.txt kwestie'
description: 'Dit artikel verstrekt een moeilijke situatie "opstellen_version.txt"is geen beschrijfbare fout wanneer het in werking stellen van het "opstelling :static-content: stelt"bevel manueel op.'
exl-id: 88d8c126-349f-49cd-8f02-2a32e4994521
feature: Deploy, Page Content, SCD
role: Developer
source-git-commit: d7c714cf5b2f9db139440d814af26c12001bb4d9
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# run `setup:static-content:deploy` distributieprobleem_version.txt

Dit artikel bevat een correctie voor `deployed_version.txt` . Dit is geen beschrijfbare fout wanneer u de opdracht `setup:static-content:deploy` handmatig uitvoert.

## Probleem

Als u de aanbevelingen van Adobe Commerce voor de infrastructuur van de cloud opvolgt om configuratiebeheer te gebruiken (en het genereren van statische elementen naar het bouwstadium te verplaatsen om de downtime van websites tijdens de implementatie te verminderen), kan de volgende fout optreden wanneer u de opdracht `setup:static-content:deploy` handmatig uitvoert:

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
