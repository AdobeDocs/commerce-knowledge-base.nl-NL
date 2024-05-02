---
title: Hoe wordt verkregen en toegepast [!UICONTROL security patch]
description: Dit artikel bevat instructies voor het verkrijgen en toepassen van een [!UICONTROL security patch] die is vrijgegeven, maar de instructies zijn niet beschikbaar.
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: b15a1d008b6cc2bdce797768e6ee7029a747e6da
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Hoe wordt een [!UICONTROL security patch]

Dit artikel bevat instructies voor het verkrijgen en toepassen van een [!UICONTROL security patch] die is vrijgegeven, maar de instructies zijn niet beschikbaar.

## Betrokken producten en versies

Adobe Commerce On-Premise en Cloud - Alle versies

## Oorzaak

Meeste [!UICONTROL Security Patches] worden vrijgegeven zonder dat er fysieke bestanden of hotfix nodig zijn.

## Oplossing


### Zaak I:

Als een fysiek patchbestand/hotfix wordt vermeld in de opmerkingen bij de release:

* Download het bestand vanuit de downloadsectie van [https://account.magento.com](https://account.magento.com/downloads/view/). (Gebruikers met gedeelde toegang moeten eerst downloadrechten krijgen van de accounteigenaar/licentiehouder.)

**Voorbehouden:**

Als u op een oudere versie van Adobe Commerce werkt en Extended Support hebt aangeschaft, moet uw versie een van de volgende opties zijn om de beveiligingspatches toe te passen:

* 2.4.2-p2
* 2.4.3-p3

Als u geen uitgebreide ondersteuning hebt, kunt u ondersteuning vragen om de patches met u te delen, maar deze kunnen geen problemen/fouten oplossen die u bij het toepassen van de patches kunt tegenkomen.

### Zaak II:

Als een fysiek patchbestand/hotfix niet wordt vermeld in de opmerkingen bij de release:

* **Wolk:**

1. Sommige [!UICONTROL Security Patches] U kunt de functie voor cloudpatches voor Commerce opnemen in of verwijderen uit de nieuwste versie van de Cloud Tools Suite (ECE Tools) - raadpleeg de [Opmerkingen bij de release](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite)en als in de release een beveiligingsoplossing wordt vermeld, voert u een upgrade van het pakket uit naar die versie.
1. Als in de opmerkingen bij de release geen melding wordt gemaakt van een beveiligingscorrectie, gaat u verder met lezen.

* **Wolk of op locatie:**

* Als er geen fysiek patchbestand/hotfix beschikbaar is, [upgrade uitvoeren van de Adobe Commerce-versie op Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X naar de nieuwste patchversie 2.4.X-pY.
* Als er geen fysiek patchbestand/hotfix beschikbaar is, [upgrade uitvoeren van de Adobe Commerce-versie op locatie](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X naar de nieuwste patchversie 2.4.X-pY.

## Gerelateerde lezing

* Zie [Opmerkingen bij de release voor de Commerce Cloud Tools Suite](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) in de *Adobe Commerce on Cloud Infrastructure Guide*.
* Zie [De Adobe Commerce-versie upgraden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) in de *Adobe Commerce on Cloud Infrastructure Guide*.
