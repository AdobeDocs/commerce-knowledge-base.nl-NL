---
title: Adobe Commerce upgrade 2.4.3, 2.3.7-p1 PHP Fatale error Hotfix
description: 'Dit artikel biedt een oplossing voor het volgende probleem: wanneer winkeliers proberen te upgraden naar Adobe Commerce (alle implementatiemethoden) of Magento Open Source 2.4.3 of 2.3.7-p1:'
exl-id: 1c472214-8387-403e-b2d2-d3f3c9e1da6a
feature: Install, Upgrade
role: Developer
source-git-commit: 1dcd003bd9b08741c0fba464f5520797cfaeccbb
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Adobe Commerce upgrade 2.4.3, 2.3.7-p1 PHP Fatale error Hotfix

Dit artikel biedt een oplossing voor het volgende probleem: wanneer winkeliers proberen te upgraden naar Adobe Commerce (alle implementatiemethoden) of Magento Open Source 2.4.3 of 2.3.7-p1:

*PHP Onherstelbare fout: Uncaught Error: Call to undefined function Magento\Framework\Filesystem\Directory\str_contains() in &lt;...>/magento/vendor/magento/framework/Filesystem/Directory/DenyListPathValidator.php:74*

De kwestie zal worden vastgesteld in het toepassingsgebied van 2.4.4, 2.4.3-p1 en 2.3.7-p2.

## Betrokken versies en producten

* Adobe Commerce (alle implementatiemethoden) bij de upgrade naar 2.3.7-p1 of 2.4.3.
* Magento Open Source bij de upgrade naar 2.3.7-p1 of 2.4.3.

## Probleem

Dit probleem wordt veroorzaakt door de nieuwe Adobe Commerce 2.4.3- en 2.3.7-p1-versies die alleen PHP 8 gebruiken, functie `str_contains` . Adobe Commerce 2.4.3 en 2.3.7-p1 zijn alleen compatibel met PHP 7.4, dus deze functie kan niet worden gebruikt.

<u> Stappen om </u> te reproduceren:

Poging om te upgraden naar Adobe Commerce 2.4.3 of 2.3.7-p1.

<u> Verwacht resultaat:</u>

Upgrade voltooid.

<u> Ware resultaat:</u>

PHP fatale fout.

## Oplossing

Als tussenoplossing voert u het volgende bevel in CLI/Terminal: `composer require symfony/polyfill-php80` van de de wortelomslag van Magento in werking of installeert een composer flard.

Om het probleem voor 2.4.3 op te lossen, moeten Adobe Commerce (alle implementatiemethoden) en Magento Open Source-handelaren een patch toepassen:

[AC-384_Fix_Incompatible_PHP_Method__2.4.3_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.4.3_ce.patch.zip)

Om het probleem voor 2.3.7-p1 op te lossen, moeten Adobe Commerce (alle implementatiemethoden) en Magento Open Source-handelaren een patch toepassen:

[AC-384_Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch.zip)

## Hoe de pleister moet worden aangebracht

Zie [ hoe te om een componentenflard toe te passen die door Magento ](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) voor instructies wordt verstrekt.

## Verwante lezing

GitHub [ Niet gestaafd PHP 8 bevel in Magento 2.4.3 EE #33680 ](https://github.com/magento/magento2/issues/33680)
