---
title: 'PWA Studio: browser geeft "Cannot proxy to"error weer'
description: Dit onderwerp bespreekt een oplossing wanneer uw Webbrowser "*Kan volmacht aan*"toont en de console toont een
exl-id: de689633-34b8-4a25-bbd0-a58742c4d03c
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# PWA Studio: browser geeft &quot;Cannot proxy to&quot;error weer

Dit onderwerp bespreekt een oplossing wanneer uw Webbrowser a &quot;*niet volmacht aan*&quot;toont en de console toont een

```
ENOTFOUND
```

fout bij het gebruiken van de Progressieve Studio van de Web App (PWA) voor Adobe Commerce.

## Betrokken producten en versies

* PWA Studio voor Adobe Commerce

## Probleem

<u> Stap om te reproduceren </u>:

* Laad uw Adobe Commerce-winkel in een browser.

<u> Verwacht resultaat </u>:

* De Adobe Commerce-winkel wordt normaal in uw browser geladen.

<u> Werkelijk resultaat </u>:

* Uw Webbrowser toont &quot;*niet volmacht aan* &quot;fout en de console toont een fout als:

```
    ENOTFOUND
```


## Oorzaak

NodeJS kan de hostnaam van uw Adobe Commerce-winkel niet oplossen.

## Oplossing

1. Zorg ervoor dat de Adobe Commerce-winkel in meerdere webbrowsers wordt geladen.
1. Als u een lokale DNS server of VPN in werking stelt, voeg een ingang aan uw hostfile (die in `/etc/hosts` wordt gevestigd) toe en kaart manueel dit domein ([ Algemene instructies op hostfile het uitgeven ](https://linuxize.com/post/how-to-edit-your-hosts-file/)) toe zodat NodeJS het kan oplossen.

## Gerelateerde lezing

* [ PWA Studio voor de Documentatie van Adobe Commerce ](https://magento.github.io/pwa-studio/)
* [ Hulpmiddelen en bibliotheken ](https://magento.github.io/pwa-studio/technologies/tools-libraries/)
