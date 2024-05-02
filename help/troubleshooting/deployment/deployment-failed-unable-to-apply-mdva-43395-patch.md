---
title: 'Implementatie mislukt: kan MDVA-43395-patch niet toepassen'
description: Dit artikel biedt een oplossing voor het probleem, waarbij het toepassen van de MDVA-43395-patch resulteert in een mislukte implementatie.
exl-id: 5341be3a-a9d7-4a4b-9755-8c585c6922a4
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
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

Cloud merchants hoeven de MDVA-43395-patch niet afzonderlijk toe te passen als ze [magento/magento-cloud-patches 1.0.16](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html#v1016) is geïnstalleerd, dat de patch al bevat.

## Oplossing

U lost dit probleem op door de patches MDVA-43395 en MDVA-43443 uit de `m2-hotfixes` directory en herimplementatie.

Als u de MDVA-43443 pleister via de `m2-hotfixes` directory, moet u deze nog steeds verwijderen zoals hierboven vermeld. In toekomstige versies van Adobe Commerce zijn deze patches al in de patches opgenomen. Hierdoor kan de implementatie mislukken als u later een upgrade uitvoert.

Als u wilt controleren of de patch is toegepast, voert u het `vendor/bin/magento-patches -n status |grep 43443` gebruiken.
Als er meerdere resultaten als deze zichtbaar zijn, dan moet u de MDVA-43443 pleister uit de `m2-hotfixes` map:

```bash
$ vendor/bin/magento-patches -n status |grep 43443
║ MDVA-43443              │ Parser token new fix                                         │ Other           │ Adobe Commerce Support │ Applied     │ Patch type: Required                                     ║
║ N/A                     │ ../m2-hotfixes/MDVA-43443_EE_2.4.2-p2_COMPOSER_v1.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                       ║
```

## Gerelateerde lezing

* [Hoe een door Adobe geleverde componentpleister aanbrengen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze kennisbasis voor ondersteuning.
* [Cloud-patches voor handel](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html#v1016) in onze ontwikkelaarsdocumentatie.
