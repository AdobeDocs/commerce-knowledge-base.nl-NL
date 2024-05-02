---
title: 'PWA Studio: Webpack loopt vast voor compilatie'
description: Dit artikel spreekt over een voorgestelde oplossing aan wanneer een javascript [Webpack] (https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack) lang alvorens met compilatie in de Progressieve Studio van de Web App (PWA Studio) te beginnen hangt.
exl-id: 692eeafa-9289-4d66-9f2f-1e0fe36e681d
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# PWA Studio: Webpack loopt vast voordat de compilatie wordt gestart

In dit artikel wordt gesproken over een voorgestelde oplossing voor het gebruik van een JavaScript [Webpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack) hangt lang alvorens met compilatie in Progressieve Studio van de Web App (PWA Studio) te beginnen.

## Betrokken producten en versies

* PWA Studio

## Probleem

[Controleer wat de meest recente release van de pawa-buildpack is](https://github.com/magento/pwa-studio/tree/master/packages/pwa-buildpack)en de

```yaml
pwa-buildpack
```

het versienummer komt naast het `package.json` bestandsnaamvermelding. Als u een oude versie van

```yaml
pwa-buildpack
```

project, kan de webpack lang hangen alvorens met compilatie te beginnen.

<u>Stappen om te reproduceren</u>:

<u>Vereisten</u>: Stel een winkelcentrum voor PWA Studio&#39;s in, zoals Venia, met een lokale Adobe Commerce-instantie en voer een

```yaml
build
```

of

```yaml
watch
```

gebruiken.

<u>Verwacht resultaat</u>:

* Als u de    ```yaml    build    ```    de bouwkunst normaal voor Venia wordt gegenereerd.
* Als u de    ```yaml    watch    ```    , start het de Venia storefront normaal.

<u>Werkelijk resultaat</u>:

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

U kunt hogere versies van OpenSSL installeren met [Homebrew](https://brew.sh/) op OSX, [Chocolatey](https://chocolatey.org/) in Windows of in het pakketbeheer van uw Linux-distributie.

## Gerelateerde lezing

* [JavaScript-webpack: concepten](https://webpack.js.org/concepts/)
* [Venia storefront setup](https://magento.github.io/pwa-studio/venia-pwa-concept/setup/)
* [PWA Buildpack](https://magento.github.io/pwa-studio/pwa-buildpack/)
* [buildpack, opdrachtregelinterface](https://magento.github.io/pwa-studio/pwa-buildpack/reference/buildpack-cli/)
* [Gereedschappen en bibliotheken: buildpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack)
