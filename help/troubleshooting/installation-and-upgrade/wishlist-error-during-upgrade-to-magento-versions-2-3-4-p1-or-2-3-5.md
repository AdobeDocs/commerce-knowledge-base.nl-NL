---
title: Fout tijdens upgraden naar Adobe Commerce versie 2.3.4-p1 of 2.3.5
description: Dit artikel biedt een oplossing voor het bekende probleem bij de upgrade naar Adobe Commerce versies 2.3.4-p1 en 2.3.5 die te maken hebben met een wishlist-fout tijdens de upgrade naar deze versies.
exl-id: 97479615-bf3f-4544-a9c1-8f19ba74318e
feature: Install, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
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

Wanneer u uw Adobe Commerce (alle implementatiemethoden) en Magento Open Source naar versie 2.3.5 of 2.3.4-p1 upgradet, kunt u een wishlist-fout (zie hieronder voor meer informatie) uit de module opvragen:

```php
Magento_Wishlist
```

De bevordering van Adobe Commerce (alle plaatsingsmethodes)/Magneto Open versie van Source 2.3.4-p1 **aan versie 2.3.4-p2** of van Adobe Commerce (alle plaatsingsmethodes)/Magneto Open versie van Source 2.3.5 **aan versie 2.3.5-p1** zal de fout bevestigen.

<u> Stappen om </u> te reproduceren:

Upgrade uw Adobe Commerce (alle implementatiemethoden)/Magento Open Source naar versie 2.3.4-p1 of 2.3.5.

<u> Verwacht resultaat </u>:

Het upgradeproces naar Adobe Commerce (alle implementatiemethoden)/Magento Open Source versie 2.3.4-p1 of 2.3.5 wordt normaal voltooid.

<u> Werkelijk resultaat </u>:

Tijdens de upgrade treedt deze fout op:

```php
Module ‘Magento_Wishlist’:

Unable to apply data patch Magento\Wishlist\Setup\Patch\Data\CleanUpData for module Magento_Wishlist. Original exception message: Unable to unserialize value. Error: Syntax error
```

## Oplossingen

* Als u aan Adobe Commerce (alle plaatsingsmethodes)/Magneto Open versie van Source 2.3.5, **verbetering aan versie 2.3.5-p1** bevorderde. Adobe Commerce (alle implementatiemethoden)/Magento Open Source versie 2.3.5-p1 vervangt 2.3.5.
* Als u aan Adobe Commerce (alle plaatsingsmethodes)/Magento Open Source versie 2.3.4-p1 bevorderde, **verbetering aan versie 2.3.4-p2**. Adobe Commerce (alle implementatiemethoden)/Magneto Open Source versie 2.3.4-p2 vervangt versie 2.3.4-p1.

## Gerelateerde lezing

In onze documentatie voor ontwikkelaars:

* [ Adobe Commerce op de gids van de wolkeninfrastructuur ](https://devdocs.magento.com/cloud/bk-cloud.html)
* [ Adobe Commerce op wolkeninfrastructuur - de versie van Adobe Commerce van de Verbetering ](https://devdocs.magento.com/cloud/project/project-upgrade.html)
* [ Adobe Commerce op-gebouw en Magento Open Source - bevorder de toepassing en de modules van Adobe Commerce ](https://devdocs.magento.com/guides/v2.3/comp-mgr/bk-compman-upgrade-guide.html)
* [ het punt van de Wijze lijst vormt pagina ](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/layouts/product-layouts.html#wishlist-item-configure-page)
* [ Modules die geavanceerde rapportering verstrekken ](https://devdocs.magento.com/guides/v2.3/advanced-reporting/modules.html)
