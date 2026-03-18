---
title: Fout tijdens upgraden naar Adobe Commerce versie 2.3.4-p1 of 2.3.5
description: Dit artikel biedt een oplossing voor het bekende probleem bij de upgrade naar Adobe Commerce versies 2.3.4-p1 en 2.3.5 die te maken hebben met een wishlist-fout tijdens de upgrade naar deze versies.
exl-id: 97479615-bf3f-4544-a9c1-8f19ba74318e
feature: Install, Upgrade
role: Developer
source-git-commit: 8be0c125bb0417e34e016656337506da88796630
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Fout tijdens upgraden naar Adobe Commerce versie 2.3.4-p1 of 2.3.5

Dit artikel biedt een oplossing voor het bekende probleem bij de upgrade naar Adobe Commerce versies 2.3.4-p1 en 2.3.5 die te maken hebben met een wishlist-fout tijdens de upgrade naar deze versies.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur 2.3.4-p1 en 2.3.5
* Adobe Commerce op locatie 2.3.4-p1 en 2.3.5

## Probleem

Wanneer u uw Adobe Commerce (alle implementatiemethoden) en Magento Open Source upgradet naar versie 2.3.5 of 2.3.4-p1, krijgt u een wishlist-fout (zie hieronder voor meer informatie) in de module:

```php
Magento_Wishlist
```

De bevordering van Adobe Commerce (alle plaatsingsmethodes)/Magneto Open versie van Source 2.3.4-p1 **aan versie 2.3.4-p2** of van Adobe Commerce (alle plaatsingsmethodes)/Magneto Open versie van Source 2.3.5 **aan versie 2.3.5-p1** zal de fout bevestigen.

<u> Stappen om </u> te reproduceren:

Upgrade uw Adobe Commerce (alle implementatiemethoden)/Magento Open Source naar versie 2.3.4-p1 of 2.3.5.

<u> Verwacht resultaat </u>:

Het upgradeproces naar Adobe Commerce (alle implementatiemethoden)/Magento Open Source versie 2.3.4-p1 of 2.3.5 wordt op de gebruikelijke wijze voltooid.

<u> Werkelijk resultaat </u>:

Tijdens de upgrade treedt deze fout op:

```php
Module ‘Magento_Wishlist’:

Unable to apply data patch Magento\Wishlist\Setup\Patch\Data\CleanUpData for module Magento_Wishlist. Original exception message: Unable to unserialize value. Error: Syntax error
```

## Oplossingen

* Als u aan Adobe Commerce (alle plaatsingsmethodes)/Magneto Open versie van Source 2.3.5, **verbetering aan versie 2.3.5-p1** bevorderde. Adobe Commerce (alle implementatiemethoden)/Magento Open Source versie 2.3.5-p1 vervangt 2.3.5.
* Als u aan Adobe Commerce (alle plaatsingsmethodes)/versie 2.3.4-p1 van Magento Open Source, **verbetering aan versie 2.3.4-p2** bevorderde. Adobe Commerce (alle implementatiemethoden)/Magneto Open Source versie 2.3.4-p2 vervangt versie 2.3.4-p1.

## Gerelateerde lezing

In onze documentatie voor ontwikkelaars:

* [&#x200B; Adobe Commerce op de gids van de wolkeninfrastructuur &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview)
* [&#x200B; Adobe Commerce op wolkeninfrastructuur - de versie van Adobe Commerce van de Verbetering &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)
* [&#x200B; Adobe Commerce op-gebouw en Magento Open Source - bevorder de toepassing en de modules van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/overview)
* [&#x200B; het punt van de Wijze lijst vormt pagina &#x200B;](https://developer.adobe.com/commerce/frontend-core/guide/layouts/product-layouts#wishlist-item-configure-page)
* [&#x200B; Modules die geavanceerde rapportering verstrekken &#x200B;](https://developer.adobe.com/commerce/php/development/advanced-reporting/modules/)
