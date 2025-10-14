---
title: De Productie van gegevens en dossiers van de synchronisatie aan het Staging of het Staging aan Integratie
description: In dit artikel wordt uitgelegd hoe u uw productieomgeving kunt synchroniseren tot Staging on Adobe Commerce op cloudinfrastructuur. Dit is niet mogelijk.
exl-id: e3d001d1-1b2a-41b5-9b4a-00e53dc9d001
feature: Integration, Build
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# De Productie van gegevens en dossiers van de synchronisatie aan het Staging of het Staging aan Integratie

In dit artikel wordt uitgelegd hoe u uw productieomgeving kunt synchroniseren naar Staging on Adobe Commerce op cloudinfrastructuur. Dit is niet mogelijk via de gebruikersinterface of de Magento-cloud-CLI.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur 2.3.x, 2.4.x

## Gegevens synchroniseren van de ene omgeving naar de andere

Als u de gegevens wilt synchroniseren, moet u de database handmatig uit de bronomgeving dumpen. Om gegevens naar een ander milieu over te brengen, moet u de bronstortplaats aan het doelmilieu dan uploaden en het invoeren. Voor meer informatie, zie [&#x200B; de Code van Adobe Commerce van de Invoer in een Project van de Wolk > het gegevensbestand van Adobe Commerce van de Invoer &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production) in onze ontwikkelaarsdocumentatie.

Voor Adobe Commerce op cloudinfrastructuur Pro kunt u ook synchroniseren van Staging en Productie naar uw integratiehoofdvertakking. Deze synchronisatie trekt en duwt slechts code, niet gegevens. Om gegevens te synchroniseren, zult u de gegevensbestandgegevens moeten dumpen en het aan het gegevensbestand van een andere milieu duwen.

>[!WARNING]
>
>Synchronisatie van de database kan niet worden uitgevoerd in de Pro Staging- en Production-clusters.

## Bestanden synchroniseren van de ene omgeving naar de andere

Gebruik de opdracht `rsync` om bestanden van de ene omgeving naar de andere te synchroniseren. Voor meer informatie, zie [&#x200B; code opstellen en statische dossiers en gegevens migreren > dossiers migreren gebruikend synchronisatie &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production#migrate-files-using-rsync) in onze ontwikkelaarsdocumentatie.

>[!NOTE]
>
>Als u de code van Integratie aan het Opvoeren wilt synchroniseren, moet u het van de tak van de Integratie doen. Voor stappen, zie [&#x200B; Synchronisatie van de ouder van het milieu &#x200B;](/docs/commerce-cloud-service/user-guide/project/console-branches.html#sync-an-environment) in onze ontwikkelaarsdocumentatie.
