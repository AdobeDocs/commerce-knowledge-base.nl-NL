---
title: Stock images not displayed, Adobe Commerce and Magento Open Source 2.3.7-p2
description: Dit artikel biedt een oplossing voor het probleem waarbij Adobe stock images die zijn geüpload naar de bestandssysteemdirectory's ` pub/media` of 'pub/media/catalog' niet worden weergegeven in de gebruikersinterface van de medialerie. De reden hiervoor is dat de afbeeldingen zich buiten de toegestane directory's van de mediagalerie bevinden. Als u deze afbeeldingen wilt weergeven, moet u de afbeeldingen op het bestandssysteem verwijderen en opnieuw uploaden naar een toegestane map in de Medialerie.
exl-id: 84488d87-095f-4739-858f-19a52d6e5822
feature: Categories, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Stock images not displayed, Adobe Commerce and Magento Open Source 2.3.7-p2

Dit artikel biedt een oplossing voor het probleem waarbij Adobe-voorraadafbeeldingen die zijn geüpload naar de bestandssysteemmappen `pub/media` of `pub/media/catalog` niet worden weergegeven in de gebruikersinterface van de medialerie. De reden hiervoor is dat de afbeeldingen zich buiten de toegestane directory&#39;s van de mediagalerie bevinden. Als u deze afbeeldingen wilt weergeven, moet u de afbeeldingen op het bestandssysteem verwijderen en opnieuw uploaden naar een toegestane map in de Medialerie.

## Betrokken producten en versies

* Adobe Commerce en Magento Open Source 2.3.7-p2


## Probleem

Handelaars kunnen Adobe Stock-afbeeldingen uploaden naar de opslagmap in de medialerie, maar deze afbeeldingen worden niet weergegeven in de gebruikersinterface en worden weergegeven alsof ze niet zijn geüpload. Dit komt omdat het systeem opmerkt dat de afbeelding al naar het bestandssysteem is geüpload, maar niet beschikbaar is in de gebruikersinterface van de medialerie. Dit betekent dat wanneer een leverancier een afbeelding uploadt naar `pub/media` of `pub/media/catalog` , deze afbeelding pas kan worden gebruikt als deze rechtstreeks in het bestandssysteem wordt verwijderd.

<u> Stappen om te reproduceren </u>

1. Schakel Adobe Stock in met geldige API-sleutels.
1. De open media galerij (**Catalogus** > **Categorieën** > **Inhoud** sectie > klikt **Uitgezocht van Galerij**).
1. Klik **Onderzoek Adobe Stock**.
1. Selecteer een afbeelding. Klik **sparen Voorproef**. Mogelijk moet u het Adobe Stock-raster opnieuw instellen om afbeeldingen weer te geven.

<u> Verwacht resultaat </u>:

De afbeelding wordt weergegeven.

<u> Werkelijk resultaat </u>:

Een foutenmelding toont: *het beeld kan niet worden gevestigd. We kunnen deze afbeelding niet vinden in de mediagalerie.*

## Oorzaak

Afbeeldingen kunnen via Adobe Stock worden geüpload naar de Opslagmap voor medialerie.

## Oplossing

Selecteer om het even welke subdirectory van de Wortel van de Opslag van de Galerij van Media (exclusief **de Wortel van de Opslag van de 0} Opslag >** Catalogus **) alvorens een beeld van Adobe Stock te uploaden.**
Schrap geüploade beelden van Adobe Stock van de `pub/media` en `pub/media/catalog` omslagen op het het dossiersysteem van Adobe Commerce en upload beelden in om het even welke toegestane subdirectories van de Root van de Opslag van de Galerij van Media in plaats daarvan (exclusief **Wortel van de Opslag** > **Catalogus**).

## Gerelateerde lezing

* [ Opslag van Media ](https://docs.magento.com/user-guide/v2.3/cms/media-storage.html) in onze gebruikersgids.
