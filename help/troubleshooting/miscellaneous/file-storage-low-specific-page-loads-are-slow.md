---
title: Bestandsopslag laag, specifieke pagina's worden traag geladen
description: Dit artikel biedt een oplossing voor het probleem van weinig schijfruimte die wordt veroorzaakt door grote, rijke afbeeldingen.
exl-id: 640c8f0d-f714-4cc1-a401-9264cfaf8e37
feature: Storage, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Bestandsopslag laag, specifieke pagina&#39;s worden traag geladen

Dit artikel biedt een oplossing voor het probleem van weinig schijfruimte die wordt veroorzaakt door grote, rijke afbeeldingen.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, alle ondersteunde versies
* Adobe Commerce, alle ondersteunde versies op locatie
* Magento Open Source, alle ondersteunde versies

## Probleem

Lage schijfopslag en trage paginabelasting kunnen worden veroorzaakt door grote, rijke afbeeldingen die veel opslagruimte gebruiken in `pub/media/catalog/products` en het delen van schijfruimte tussen ophaling en productie (tenzij een specifieke opvoeromgeving is ingericht).

## Oorzaak

Afbeeldingen zijn niet geoptimaliseerd om de prestaties in evenwicht te brengen met de weergavekwaliteit.

## Oplossing

Voordat u afbeeldingen uploadt, optimaliseert en comprimeert u deze om de prestaties in evenwicht te brengen met de weergavekwaliteit. Hierdoor neemt de ruimte toe en nemen de laadtijden van de pagina af. PNG-bestanden geven kleinere afmetingen voor afbeeldingen met grote gebieden met effen kleuren. JPEG geven kleinere grootten voor alle andere zaken. Gebruik de hoogste compressie (zonder merkbare verslechtering). Dit is meestal 60-80%.

Het gebruik [ snelst beeldoptimalisering ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html?lang=nl-NL) om opslag efficiëntere beelden te produceren.

## Gerelateerde lezing

Om over het beheren van uw schijfruimte (als u op Adobe Commerce op wolkeninfrastructuur) bent te leren zie [ schijfruimte in Adobe Commerce beheren ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html?lang=nl-NL) in Commerce op de Gids van de Infrastructuur van de Wolk.
