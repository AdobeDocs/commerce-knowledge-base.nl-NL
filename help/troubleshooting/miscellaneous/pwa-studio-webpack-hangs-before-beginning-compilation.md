---
title: 'PWA Studio: Webpack loopt vast voordat de compilatie wordt gestart'
description: Dit artikel spreekt over een voorgestelde oplossing aan wanneer een javascript [Webpack] (https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/#webpack) lang alvorens met compilatie in de Progressieve Studio van de Web App (PWA Studio) te beginnen hangt.
exl-id: 692eeafa-9289-4d66-9f2f-1e0fe36e681d
feature: Configuration
role: Developer
source-git-commit: 032fe4d32921c63570672b9c68e8c03e00bd1077
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# PWA Studio: Webpack loopt vast voordat de compilatie wordt gestart

Dit artikel spreekt over een voorgestelde oplossing aan wanneer een javascript [ Webpack ](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/#webpack) lange tijd alvorens met compilatie in de Progressieve Studio van de Web App (PWA Studio) te beginnen hangt.

## Betrokken producten en versies

* PWA Studio

## Probleem

[ Controle wat de recentste versie van pwa-buildpack is ](https://github.com/magento/pwa-studio/tree/master/packages/pwa-buildpack), en

```yaml
pwa-buildpack
```

naast de bestandsnaamlijst van `package.json` staat een versienummer. Als u een oude versie van

```yaml
pwa-buildpack
```

project, kan de webpack lang hangen alvorens met compilatie te beginnen.

<u> Stappen om </u> te reproduceren:

<u> Eerste vereisten </u>: Opstelling een storefront van PWA Studio, zoals Venia, met een lokale instantie van Adobe Commerce en stel a in werking

```yaml
build
```

of

```yaml
watch
```

gebruiken.

<u> Verwacht resultaat </u>:

* Als u de    ```yaml    build    ```    de bouwkunst normaal voor Venia wordt gegenereerd.
* Als u de    ```yaml    watch    ```    , start het de Venia storefront normaal.

<u> Werkelijk resultaat </u>:

Uw

```yaml
build
```

of

```yaml
watch
```

het bevel zal worden vastgezet en zal niet voltooien, noch zullen om het even welke fouten worden getoond.

## Oplossingen

Werk uw project bij gebruikend het volgende bevel:

```yaml
yarn upgrade
```

Zorg ervoor u een huidige versie van open op uw systeem gebruikend het volgende bevel hebt:

```yaml
openssl version
```

De versie moet 1.0 of hoger zijn (of LibreSSL 2, in het geval van OSX High Sierra.).

U kunt hogere versies van OpenSSL met [ Homebrew ](https://brew.sh/) op OSX, [ Chocolade ](https://chocolatey.org/) op Vensters, of uw het pakketmanager van de distributie van Linux installeren.

## Gerelateerde lezing

* [ JavaScript Webpack: Concepten ](https://webpack.js.org/concepts/)
* [ Venia storefront opstelling ](https://developer.adobe.com/commerce/pwa-studio/guides/packages/venia/)
* [ PWA Buildpack ](https://developer.adobe.com/commerce/pwa-studio/guides/packages/buildpack/)
* [ bouwdpack Interface van de Lijn van het Bevel ](https://developer.adobe.com/commerce/pwa-studio/api/buildpack/cli/)
* [ Hulpmiddelen en bibliotheken: bouwstijlpak ](https://developer.adobe.com/commerce/pwa-studio/guides/project/tools-libraries/#webpack)
