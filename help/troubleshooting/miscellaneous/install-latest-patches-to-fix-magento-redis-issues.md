---
title: Nieuwste patches installeren om Adobe Commerce Redis-problemen op te lossen
description: Dit artikel bevat informatie over de nieuwste Redis-patches die beschikbaar zijn in het pakket [Adobe Commerce on cloud Infrastructure Patches](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).
exl-id: 0335bc11-f679-4629-b4e7-6a0e68c3ae44
feature: Cache, Install, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Nieuwste patches installeren om Adobe Commerce Redis-problemen op te lossen

Dit artikel verstrekt informatie over de recentste Redis-Verwante flarden beschikbaar in [&#x200B; Adobe Commerce op het pakket van de Patches van de wolkeninfrastructuur &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches).

## Betrokken producten en versies

Adobe Commerce over wolkeninfrastructuur 2.3.3, 2.3.4

## Probleem

Het extra CPU- en geheugenverbruik van Redis kan de Adobe Commerce-prestaties en dus ook de algemene prestaties van uw website verminderen.

## Oplossing

Pas de nieuwste patches van Adobe Commerce toe op het patchpakket voor cloudinfrastructuur. Voor gedetailleerde instructies, verwijs naar [&#x200B; passen flarden &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

De nieuwste Redis-patches die door Adobe Commerce zijn geleverd op het patches-pakket voor cloudinfrastructuur, dragen bij aan het volgende:

* het verminderen van de grootte van voorzien van een netwerkmededeling voor Redis
* vaststelling van renderomstandigheden die leiden tot extra geheugenverbruik
* de adapter van het Geheime voorgeheugen veranderen om uitzettingsgevallen te behandelen
* Verlaagd CPU-verbruik Redis

Adobe Commerce raadt ook aan een upgrade naar Redis 5 uit te voeren als u Adobe Commerce op cloudinfrastructuur 2.3.3 of hoger uitvoert.
