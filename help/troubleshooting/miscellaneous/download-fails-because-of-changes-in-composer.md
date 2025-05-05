---
title: Downloaden mislukt vanwege wijzigingen in Composer
description: Dit artikel bevat een oplossing voor een gedownloade Adobe Commerce-download en een uitzonderingsfout.
exl-id: 5abdab97-4b0c-466b-a68f-a2637d2826e5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Downloaden mislukt vanwege wijzigingen in Composer

Dit artikel bevat een oplossing voor een gedownloade Adobe Commerce-download en een uitzonderingsfout.

## Probleem

Tijdens het downloaden wordt de volgende fout weergegeven:

```php
[ErrorException]
  file_get_contents(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## Oorzaak

Dit is het gevolg van wijzigingen in bepaalde versies van Composer. Als tussenoplossing kunt u Composer naar een eerdere versie downgraden en de Adobe Commerce-download opnieuw proberen.

## Oplossing

Elke versie van Composer van 21 november tot 26 november 2015 heeft dit probleem. Voer de volgende opdracht in om te bevestigen dat dit probleem gerelateerd is aan de Composer-versie:

```php
composer -v
```

De versie ziet er ongeveer als volgt uit:

```php
Composer version 1.0-dev (2b14f0a047dd4f3545ec82381f65c36ea93a4c81) 2015-11-25 17:13:09
```

Merk op dat de datum 2015-11-25 is, die aangeeft dat Composer dit probleem heeft.

U kunt als volgt rondom de achtergrond werken:

1. Wijzig uw versie van Composer zodat u de Adobe Commerce-software kunt downloaden door een van de volgende handelingen uit te voeren:

   * Composer downgraden met de volgende opdracht: `composer self-update 1.0.0-alpha11` .
   * Upgrade Composer naar een versie die ouder is dan 26 november 2015: `composer self-update` .

1. Verwijder de Adobe Commerce-map en -submappen.
1. Probeer de download opnieuw met `[composer create-project](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/composer)` of `[git clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)` .
1. Werk de Composer bij nadat het downloaden van de Adobe Commerce-software is voltooid: `composer self-update`.
