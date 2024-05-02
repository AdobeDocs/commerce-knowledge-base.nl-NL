---
title: Nieuwste patches installeren om Adobe Commerce Redis-problemen op te lossen
description: Dit artikel bevat informatie over de nieuwste Redis-patches die beschikbaar zijn in het pakket [Adobe Commerce on cloud Infrastructure Patches](https://devdocs.magento.com/cloud/project/project-patch.html).
exl-id: 0335bc11-f679-4629-b4e7-6a0e68c3ae44
feature: Cache, Install, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Nieuwste patches installeren om Adobe Commerce Redis-problemen op te lossen

Dit artikel bevat informatie over de meest recente Redis-gerelateerde patches die beschikbaar zijn in [Adobe Commerce on cloud Infrastructure Patches](https://devdocs.magento.com/cloud/project/project-patch.html) pakket.

## Betrokken producten en versies

Adobe Commerce over wolkeninfrastructuur 2.3.3, 2.3.4

## Probleem

Het extra CPU- en geheugenverbruik van Redis kan de Adobe Commerce-prestaties en dus ook de algemene prestaties van uw website verminderen.

## Oplossing

Pas de nieuwste patches van Adobe Commerce toe op het patchpakket voor cloudinfrastructuur. Zie voor gedetailleerde instructies [Patches toepassen](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

De nieuwste Redis-patches die door Adobe Commerce zijn geleverd op het patches-pakket voor cloudinfrastructuur, dragen bij aan het volgende:

* het verminderen van de grootte van voorzien van een netwerkmededeling voor Redis
* vaststelling van renderomstandigheden die leiden tot extra geheugenverbruik
* de adapter van het Geheime voorgeheugen veranderen om uitzettingsgevallen te behandelen
* Verlaagd CPU-verbruik Redis

Adobe Commerce raadt ook aan een upgrade naar Redis 5 uit te voeren als u Adobe Commerce op cloudinfrastructuur 2.3.3 of hoger uitvoert.
