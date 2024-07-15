---
title: Procedure voor ophalen en toepassen [!UICONTROL security patch]
description: Dit artikel bevat instructies voor het ophalen en toepassen van een vrijgegeven [!UICONTROL security patch] , maar instructies zijn niet beschikbaar.
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: b15a1d008b6cc2bdce797768e6ee7029a747e6da
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Een [!UICONTROL security patch] ophalen en toepassen

Dit artikel bevat instructies voor het ophalen en toepassen van een vrijgegeven [!UICONTROL security patch] , maar instructies zijn niet beschikbaar.

## Betrokken producten en versies

Adobe Commerce On-Premise en Cloud - Alle versies

## Oorzaak

De meeste [!UICONTROL Security Patches] worden vrijgegeven zonder fysieke bestanden of hotfix die moeten worden toegepast.

## Oplossing


### Zaak I:

Als een fysiek patchbestand/hotfix wordt vermeld in de opmerkingen bij de release:

* Download het dossier van de downloadsectie van [ https://account.magento.com ](https://account.magento.com/downloads/view/). (Gebruikers met gedeelde toegang moeten eerst downloadrechten krijgen van de accounteigenaar/licentiehouder.)

**beveats:**

Als u op een oudere versie van Adobe Commerce werkt en Extended Support hebt aangeschaft, moet uw versie een van de volgende opties zijn om de beveiligingspatches toe te passen:

* 2.4.2-p2
* 2.4.3-p3

Als u geen uitgebreide ondersteuning hebt, kunt u ondersteuning vragen om de patches met u te delen, maar deze kunnen geen problemen/fouten oplossen die u bij het toepassen van de patches kunt tegenkomen.

### Zaak II:

Als een fysiek patchbestand/hotfix niet wordt vermeld in de opmerkingen bij de release:

* **Wolk:**

1. Sommige [!UICONTROL Security Patches] zouden in de recentste versie van de Reeks van Hulpmiddelen van de Wolk (ECE Hulpmiddelen) onder de Patches van de Wolk voor Commerce kunnen worden omvat/worden vrijgegeven - controleer de [ Nota&#39;s van de Versie ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite), en als een veiligheidsmoeilijke situatie in de versie wordt vermeld, bevorder het pakket aan die versie.
1. Als in de opmerkingen bij de release geen melding wordt gemaakt van een beveiligingscorrectie, gaat u verder met lezen.

* **Wolk of op-Premise:**

* Als een fysiek flarddossier/hotfix niet beschikbaar is, [ bevorder de versie van Adobe Commerce op Wolk ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X aan recentste flardversie 2.4.X-pY.
* Als een fysiek flarddossier/hotfix niet beschikbaar is, [ bevorder de versie van Adobe Commerce On-Premise ](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X aan recentste flardversie 2.4.X-pY.

## Gerelateerde lezing

* Zie {de nota&#39;s van de Versie voor de Reeks van Hulpmiddelen van de Commerce Cloud ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) in *Adobe Commerce op de Gids van de Infrastructuur van de Wolk*.[
* Zie [ de versie van Adobe Commerce ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) in *Adobe Commerce op de Gids van de Infrastructuur van de Wolk* bevorderen.
