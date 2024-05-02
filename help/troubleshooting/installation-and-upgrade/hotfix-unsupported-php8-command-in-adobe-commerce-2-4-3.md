---
title: Adobe Commerce upgrade 2.4.3, 2.3.7-p1 PHP Fatale error Hotfix
description: 'Dit artikel biedt een oplossing voor het volgende probleem: wanneer handelaren proberen te upgraden naar Adobe Commerce (alle implementatiemethoden) of Magento Open Source 2.4.3 of 2.3.7-p1:'
exl-id: 1c472214-8387-403e-b2d2-d3f3c9e1da6a
feature: Install, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Adobe Commerce upgrade 2.4.3, 2.3.7-p1 PHP Fatale error Hotfix

Dit artikel biedt een oplossing voor het volgende probleem: wanneer winkeliers proberen te upgraden naar Adobe Commerce (alle implementatiemethoden) of Magento Open Source 2.4.3 of 2.3.7-p1:

*Fatale fout in PHP: Uncaught Error: Call to undefined function Magento\Framework\Filesystem\Directory\str_contains() in &lt;..>/magento/vendor/magento/framework/Filesystem/Directory/DenyListPathValidator.php:74*

De kwestie zal worden vastgesteld in het toepassingsgebied van 2.4.4, 2.4.3-p1 en 2.3.7-p2.

## Betrokken versies en producten

* Adobe Commerce (alle implementatiemethoden) bij de upgrade naar 2.3.7-p1 of 2.4.3.
* Magento Open Source bij de upgrade naar 2.3.7-p1 of 2.4.3.

## Probleem

Dit probleem wordt veroorzaakt door de nieuwe Adobe Commerce 2.4.3 en 2.3.7-p1 versies die alleen PHP 8 gebruiken `str_contains`. Adobe Commerce 2.4.3 en 2.3.7-p1 zijn alleen compatibel met PHP 7.4, dus deze functie kan niet worden gebruikt.

<u>Stappen om te reproduceren</u> :

Poging om te upgraden naar Adobe Commerce 2.4.3 of 2.3.7-p1.

<u>Verwacht resultaat:</u>

Upgrade voltooid.

<u>Werkelijk resultaat:</u>

PHP fatale fout.

## Oplossing

Als alternerende actie stelt u het volgende bevel in CLI/Terminal in werking: `composer require symfony/polyfill-php80` in de hoofdmap van het Magento of installeer een componentpatch.

Om het probleem voor 2.4.3 op te lossen, moeten Adobe Commerce (alle implementatiemethoden) en Magento Open Source handelaren een patch toepassen:

[AC-384_Fix_Incompatible_PHP_Method__2.4.3_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.4.3_ce.patch.zip)

Om het probleem voor 2.3.7-p1 op te lossen, moeten Adobe Commerce (alle implementatiemethoden) en Magento Open Source-handelaren een patch toepassen:

[AC-384_Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch.zip)

## Hoe de pleister moet worden aangebracht

Zie [Hoe een door het Magento geleverde componentpleister aanbrengen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies.

## Verwante lezing

GitHub [Niet-ondersteunde PHP 8-opdracht in Magento 2.4.3 EE #33680](https://github.com/magento/magento2/issues/33680)
