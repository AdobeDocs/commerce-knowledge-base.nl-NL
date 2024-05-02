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

Dit artikel biedt een oplossing voor het probleem waarbij Adobe-voorraadafbeeldingen worden geüpload naar de mappen van het bestandssysteem `pub/media` of `pub/media/catalog` niet weergeven in de gebruikersinterface van de medialerie. De reden hiervoor is dat de afbeeldingen zich buiten de toegestane directory&#39;s van de mediagalerie bevinden. Als u deze afbeeldingen wilt weergeven, moet u de afbeeldingen op het bestandssysteem verwijderen en opnieuw uploaden naar een toegestane map in de Medialerie.

## Betrokken producten en versies

* Adobe Commerce en Magento Open Source 2.3.7-p2


## Probleem

Handelaars kunnen Adobe Stock-afbeeldingen uploaden naar de opslagmap in de medialerie, maar deze afbeeldingen worden niet weergegeven in de gebruikersinterface en worden weergegeven alsof ze niet zijn geüpload. Dit komt omdat het systeem opmerkt dat de afbeelding al naar het bestandssysteem is geüpload, maar niet beschikbaar is in de gebruikersinterface van de medialerie. Dit betekent dat wanneer een handelaar een afbeelding uploadt naar `pub/media` of `pub/media/catalog`, kunnen ze die afbeelding pas gebruiken nadat deze rechtstreeks in het bestandssysteem is verwijderd.

<u>Stappen om te reproduceren</u>

1. Schakel Adobe Stock in met geldige API-sleutels.
1. Mediagalerie openen (**Catalogus** > **Categorieën** > **Inhoud** sectie > klikken **Selecteren in galerie**).
1. Klikken **Zoeken in Adobe Stock**.
1. Selecteer een afbeelding. Klik **Voorvertoning opslaan**. Mogelijk moet u het Adobe Stock-raster opnieuw instellen om afbeeldingen weer te geven.

<u>Verwacht resultaat</u>:

De afbeelding wordt weergegeven.

<u>Werkelijk resultaat</u>:

Er wordt een foutbericht weergegeven: *De afbeelding kan niet worden gevonden. Deze afbeelding kan niet worden gevonden in de mediagalerie.*

## Oorzaak

Afbeeldingen kunnen via Adobe Stock worden geüpload naar de Opslagmap voor medialerie.

## Oplossing

Selecteer een submap van de Opslagmap voor medialerie (exclusief **Opslaghoofdmap** > **Catalogus**) voordat u een Adobe Stock-afbeelding uploadt.
Geüploade Adobe Stock-afbeeldingen verwijderen uit het dialoogvenster `pub/media` en `pub/media/catalog` mappen op het Adobe Commerce-bestandssysteem en in plaats daarvan afbeeldingen uploaden naar toegestane submappen voor Media Gallery Storage Root (exclusief **Opslaghoofdmap** > **Catalogus**).

## Gerelateerde lezing

* [Media-opslag](https://docs.magento.com/user-guide/v2.3/cms/media-storage.html) in onze gebruikershandleiding.
