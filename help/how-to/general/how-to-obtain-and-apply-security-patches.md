---
title: Procedure voor ophalen en toepassen [!UICONTROL security patch]
description: Dit artikel bevat instructies voor het ophalen en toepassen van een vrijgegeven [!UICONTROL security patch] , maar instructies zijn niet beschikbaar.
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: 3c7234b52e5e4465d95c95345e1c070c28600dfb
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# Een [!UICONTROL security patch] ophalen en toepassen

>[!NOTE]
>Als u een installatie op locatie hebt en geen versiebeheersystemen zoals [!DNL CVS] of [!DNL GitHub] gebruikt om uw code te beheren, kan uw webhost u mogelijk helpen bij het toepassen van de patch. Voel je vrij om hen te bereiken voor steun.

Dit artikel bevat instructies voor het ophalen en toepassen van een vrijgegeven [!UICONTROL security patch] , maar instructies zijn niet beschikbaar.

## Betrokken producten en versies

Adobe Commerce On-Premise en Cloud - Alle versies


## Oorzaak

De meeste [!UICONTROL Security Patches] worden vrijgegeven zonder afzonderlijke patch of hotfix en moeten worden bijgewerkt naar de release van [!UICONTROL Security Patch] .

## Oplossing


### Zaak I:

* Als een geïsoleerd flarddossier/hotfix in de [&#x200B; Nota&#39;s van de Versie &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/release-notes/cloud-tools-suite) wordt vermeld download het dossier van de downloadsectie van [&#x200B; https://account.magento.com &#x200B;](https://account.magento.com/downloads/view/). Gebruikers met gedeelde toegang moeten eerst downloadrechten krijgen van de eigenaar/licentiehouder van de account.

**beveats:**

Als u op een oudere versie van Adobe Commerce (2.4.4) werkt, hebt u automatisch Extended Support ontvangen. Uw versie moet een van de volgende niet-ondersteunde versies zijn om de nieuwste beschikbare beveiligingspatches toe te passen:

2.4.4 - 2.4.4-p11

Niet-ondersteunde versies (2.3.x, 2.4.0 - 2.4.3) komen niet in aanmerking voor ondersteuning en u moet eerst een upgrade uitvoeren naar een ondersteunde versie om te profiteren van de meest recente beveiligingsoplossingen.

Als u geen uitgebreide ondersteuning hebt, kunt u ondersteuning vragen om de patches met u te delen, maar deze kunnen geen problemen/fouten oplossen die u bij het toepassen van de patches kunt tegenkomen.

### Zaak II:

Geïsoleerde patches worden alleen in uitzonderlijke gevallen geleverd, en het is niet de voorkeursvorm voor het implementeren van beveiligingsoplossingen.

Als een afzonderlijk patchbestand/hotfix niet wordt vermeld in de opmerkingen bij de release:

* **Wolk:**

1. Sommige [!UICONTROL Security Patches] zouden in de recentste versie van de Reeks van Hulpmiddelen van de Wolk (ECE Hulpmiddelen) onder de Patches van de Wolk voor Commerce kunnen worden omvat/worden vrijgegeven - controleer de [&#x200B; Nota&#39;s van de Versie &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite), en als een veiligheidsmoeilijke situatie in de versie wordt vermeld, bevorder het pakket aan die versie.
1. Als in de opmerkingen bij de release geen melding wordt gemaakt van een beveiligingscorrectie, gaat u verder met lezen.

* **Wolk of op-Premise:**

* Als een geïsoleerd flarddossier/hotfix niet beschikbaar is, [&#x200B; bevorder de versie van Adobe Commerce op Wolk &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X aan recentste flardversie 2.4.X-pY.
* Als een geïsoleerd flarddossier/hotfix niet beschikbaar is, [&#x200B; bevorder de versie van Adobe Commerce On-Premise &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X aan recentste flardversie 2.4.X-pY.

## Gerelateerde lezing

* Zie [&#x200B; de nota&#39;s van de Versie voor de Reeks van Commerce Cloud Tools &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) in *Adobe Commerce op de Gids van de Infrastructuur van de Wolk*.
* Zie [&#x200B; de versie van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) in *Adobe Commerce op de Gids van de Infrastructuur van de Wolk* bevorderen.
