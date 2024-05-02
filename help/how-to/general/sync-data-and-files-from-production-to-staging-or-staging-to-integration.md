---
title: De Productie van gegevens en dossiers van de synchronisatie aan het Staging of het Staging aan Integratie
description: In dit artikel wordt uitgelegd hoe u uw productieomgeving kunt synchroniseren tot Staging on Adobe Commerce op cloudinfrastructuur. Dit is niet mogelijk.
exl-id: e3d001d1-1b2a-41b5-9b4a-00e53dc9d001
feature: Integration, Build
source-git-commit: ef294ddc9c4a12b06ce7738cb4702253dd892f3b
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# De Productie van gegevens en dossiers van de synchronisatie aan het Staging of het Staging aan Integratie

In dit artikel wordt uitgelegd hoe u uw productieomgeving kunt synchroniseren naar Staging on Adobe Commerce op cloudinfrastructuur. Dit is niet mogelijk via de gebruikersinterface of de Magento-cloud-CLI.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur 2.3.x, 2.4.x

## Gegevens synchroniseren van de ene omgeving naar de andere

Als u de gegevens wilt synchroniseren, moet u de database handmatig uit de bronomgeving dumpen. Om gegevens naar een ander milieu over te brengen, moet u de bronstortplaats aan het doelmilieu dan uploaden en het invoeren. Zie voor meer informatie [Adobe Commerce-code importeren in een Cloud-project > Adobe Commerce-database importeren](https://devdocs.magento.com/cloud/setup/first-time-setup-import-import.html) in onze ontwikkelaarsdocumentatie.

Voor Adobe Commerce op cloudinfrastructuur Pro kunt u ook synchroniseren van Staging en Productie naar uw integratiehoofdvertakking. Deze synchronisatie trekt en duwt slechts code, niet gegevens. Om gegevens te synchroniseren, zult u de gegevensbestandgegevens moeten dumpen en het aan het gegevensbestand van een andere milieu duwen.

>[!WARNING]
>
>Synchronisatie van de database kan niet worden uitgevoerd in de Pro Staging- en Production-clusters.

## Bestanden synchroniseren van de ene omgeving naar de andere

Als u bestanden wilt synchroniseren van de ene omgeving naar de andere, gebruikt u de opdracht `rsync` gebruiken. Zie voor meer informatie [Code implementeren en statische bestanden en gegevens migreren > Bestanden migreren via synchronisatie](https://devdocs.magento.com/cloud/live/stage-prod-migrate.html#migrate-files-using-rsync) in onze ontwikkelaarsdocumentatie.

>[!NOTE]
>
>Als u de code van Integratie aan het Opvoeren wilt synchroniseren, moet u het van de tak van de Integratie doen. Zie voor stappen [Synchroniseren met de bovenliggende omgeving](/docs/commerce-cloud-service/user-guide/project/console-branches.html#sync-an-environment) in onze ontwikkelaarsdocumentatie.
