---
title: 'Implementatie mislukt: kan de MDVA-43395-patch niet toepassen'
description: Dit artikel biedt een oplossing voor het probleem, waarbij het toepassen van de MDVA-43395-patch resulteert in een mislukte implementatie.
exl-id: 5341be3a-a9d7-4a4b-9755-8c585c6922a4
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Implementatie mislukt: kan de MDVA-43395-patch niet toepassen

Dit artikel biedt een oplossing voor het probleem, waarbij het toepassen van de MDVA-43395-patch resulteert in een mislukte implementatie.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur (alle versies)

## Probleem

U kunt de MDVA-43395-pleister niet aanbrengen.

## Oorzaak

De kooplieden van de wolk hoeven niet om het flard MDVA-43395 afzonderlijk toe te passen als zij [ magento/magento-cloud-patches 1.0.16 ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches#v1016) geïnstalleerd hebben, die reeds het flard omvat.

## Oplossing

U lost het probleem op door de patches MDVA-43395 en MDVA-43443 uit de map `m2-hotfixes` te verwijderen en opnieuw te implementeren.

Als u de MDVA-43443-patch via de map `m2-hotfixes` kon toepassen, moet u de patch toch verwijderen, zoals hierboven vermeld. In toekomstige versies van Adobe Commerce zijn deze patches al in de patches opgenomen. Hierdoor kan de implementatie mislukken als u later een upgrade uitvoert.

Voer de opdracht `vendor/bin/magento-patches -n status |grep 43443` uit om te controleren of de patch is toegepast.
Als er meerdere resultaten als deze worden weergegeven, verwijdert u de MDVA-43443-patch uit de map `m2-hotfixes` :

```bash
$ vendor/bin/magento-patches -n status |grep 43443
║ MDVA-43443              │ Parser token new fix                                         │ Other           │ Adobe Commerce Support │ Applied     │ Patch type: Required                                     ║
║ N/A                     │ ../m2-hotfixes/MDVA-43443_EE_2.4.2-p2_COMPOSER_v1.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                       ║
```

## Gerelateerde lezing

* [ hoe te om een componentenflard toe te passen dat door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze steunkennisbasis wordt verstrekt.
* [ de Patches van de Wolk voor Commerce ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches#v1016) in onze ontwikkelaarsdocumentatie.
