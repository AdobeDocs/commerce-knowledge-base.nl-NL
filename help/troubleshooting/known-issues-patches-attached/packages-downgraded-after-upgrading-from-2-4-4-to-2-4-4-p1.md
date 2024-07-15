---
title: Pakketten die na een upgrade zijn gedowngraded van 2.4.4 naar 2.4.4-p1
description: Dit artikel biedt een hotfix voor het probleem wanneer verkopers op versie 2.4.4 de opdracht 'composer update' uitvoeren en de hieronder vermelde pakketten (modules) naar hun eerdere versies worden gedowngraded, die niet compatibel zijn met versie 2.4.4 en alleen worden geacht te worden gebruikt met versie 2.4.5 en hoger.
exl-id: 4ebdbcd7-6905-4647-b071-1e4413455f38
feature: Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---

# Pakketten die na een upgrade zijn gedowngraded van 2.4.4 naar 2.4.4-p1

Dit artikel bevat een hotfix voor het probleem wanneer verkopers op versie 2.4.4 de opdracht `composer update` uitvoeren en de hieronder vermelde pakketten (modules) naar hun eerdere versies worden gedowngraded, die niet compatibel zijn met versie 2.4.4 en alleen worden gebruikt met versie 2.4.5 en hoger.

## Betrokken producten en versies

* Adobe Commerce over wolkeninfrastructuur 2.4.4
* Adobe Commerce op locatie 2.4.4
* Magento Open Source 2.4.4

## Probleem

Er zijn twee scenario&#39;s hoe deze kwestie kan voorkomen en hoe het kan worden gereproduceerd:

### Scenario 1

<u> Stappen om </u> te reproduceren:

Bij een upgrade van 2.4.4 naar 2.4.4-p1 is er een aantal pakketten (modules) die met een vergelijkbare uitvoer zijn gedowngradeerd:

```text
Downgrading magento/module-adobe-ims (2.1.4 => 2.1.3)
Downgrading magento/module-adobe-ims-api (2.1.2 => 2.1.1)
Downgrading magento/module-adobe-stock-admin-ui (1.3.2 => 1.3.1)
Downgrading magento/module-adobe-stock-client-api (2.1.2 => 2.1.1)
Downgrading magento/module-adobe-stock-image (1.3.3 => 1.3.2)
Downgrading magento/module-adobe-stock-image-admin-ui (1.3.3 => 1.3.2)
Downgrading magento/module-banner-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-inventory (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-advanced-checkout (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-api (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-bundle-product (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-catalog-api (1.3.3 => 1.3.2)
Downgrading magento/module-inventory-configurable-product-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-configurable-product-frontend-ui (1.0.3 => 1.0.2)
Downgrading magento/module-inventory-import-export (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-in-store-pickup-admin-ui (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-in-store-pickup-frontend (1.1.3 => 1.1.2)
Downgrading magento/module-inventory-in-store-pickup-graph-ql (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-in-store-pickup-sales-admin-ui (1.1.3 => 1.1.2-p1)
Downgrading magento/module-inventory-in-store-pickup-shipping (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-low-quantity-notification (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-low-quantity-notification-api (1.2.2 => 1.2.1-p1)
Downgrading magento/module-inventory-requisition-list (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-sales-admin-ui (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-sales-api (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-shipping-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-source-selection-api (1.4.2 => 1.4.1-p1)
Downgrading magento/module-inventory-wishlist (1.0.2 => 1.0.1)
Downgrading magento/module-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-re-captcha-checkout-sales-rule (1.1.1 => 1.1.0)
Downgrading magento/module-re-captcha-customer (1.1.3 => 1.1.2)
Downgrading magento/module-re-captcha-frontend-ui (1.1.3 => 1.1.2)
Downgrading magento/module-staging-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-two-factor-auth (1.1.4 => 1.1.3)
Removing magento/module-admin-adobe-ims (100.4.0)
```

<u> Verwachte resultaten </u>:

De upgrade van versie 2.4.4 naar 2.4.4-p1 resulteert in de juiste pakketten (modules) voor versie 2.4.4-p1.

<u> Ware resultaten </u>:

Tijdens de verbetering van versie 2.4.4 aan 2.4.4-p1, degraderen deze de versies van deze pakketten (modules&#39;), maar deze berichten kunnen worden genegeerd, en de functionaliteit wordt niet beïnvloed.

### Scenario 2

<u> Stappen om </u> te reproduceren:

Wanneer 2.4.4 handelaars het `composer update` bevel in werking stellen, dan de zelfde pakketten (modules) hierboven in **Scenario 1** worden bevorderd aan hun nieuwere versies die slechts met versie 2.4.5 compatibel zijn en niet verondersteld om met versie 2.4.4 worden gebruikt.

<u> Verwachte resultaten </u>:

De upgrade van versie 2.4.4 naar 2.4.4-p1 resulteert in de juiste pakketten (modules) voor versie 2.4.4-p1.

<u> Ware resultaten </u>:

Pakketten (modules) worden na de upgrade gedowngraded van versie 2.4.4 naar 2.4.4-p1.

## Workaround 1: Patch

De patch is aan dit artikel gekoppeld. Om het te downloaden, scrol neer aan het eind van het artikel en klik het dossier - noem of klik de volgende verbinding: [ Download ACPLTSRV-2017-fix.sh.zip ](assets/ACPLTSRV-2017-fix.sh.zip)

## Compatibele Adobe Commerce- en Magento Open Source-versies:

De patch is gemaakt voor:

* Adobe Commerce over wolkeninfrastructuur 2.4.4
* Adobe Commerce op locatie 2.4.4
* Magento Open Source 2.4.4

>[!NOTE]
>
>De patch is niet compatibel met andere Adobe Commerce- en Magento Open Source-versies en -versies.

## Hoe de pleister moet worden aangebracht

Gebruik het bash manuscript in bijlage [ ACPLTSRV-2017-fix.sh.zip ](assets/ACPLTSRV-2017-fix.sh.zip) als alternerende actie voor deze kwestie.

**Exacte instructies hoe te om het manuscript te gebruiken:**

### Op Adobe Commerce over cloudinfrastructuur:

1. Download het basscript-bestand `ACPLTSRV-2017-fix.sh` naar uw lokale uitchecking van uw cloudcodebase.
1. Voer het basscript-bestand `ACPLTSRV-2017-fix.sh` uit om de composer-bestanden lokaal te wijzigen.
1. Voeg de gewijzigde composer-bestanden toe aan en wijs deze toe aan uw it-opslagplaats.

### Op Adobe Commerce of Magento Open Source ter plaatse:

1. Plaats het basscript `ACPLTSRV-2017-fix.sh` in de map `root` van de installatie van Adobe Commerce/Magento Open Source 2.4.4 (dezelfde map als de `composer.json` ).
1. Voer het basscript uit met een argument `apply` om de desbetreffende pakketten (modules) te vergrendelen op hun 2.4.4-versies:

   ```bash
   sh ACPLTSRV-2017-fix.sh apply
   ```

1. Composer uitvoeren bijgewerkt om de vergrendelde pakketten (modules) te installeren.
1. Wanneer u gereed bent om te upgraden naar 2.4.5 of 2.4.4-p1, voert u het script uit met een argument `rollback` :

   ```bash
   sh ACPLTSRV-2017-fix.sh rollback
   ```

   Als u deze stap overslaat, treden upgradefouten op als gevolg van conflicterende pakketten (modules).
1. Nadat u de bovenstaande stappen hebt uitgevoerd, kunt u een upgrade uitvoeren.

## Workaround 2

De tweede oplossing voor dit probleem is niet de opdracht `composer update` zonder argumenten uit te voeren.
