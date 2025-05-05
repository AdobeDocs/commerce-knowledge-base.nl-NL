---
title: Index is vergrendeld door een ander proces
description: In dit artikel wordt gesproken over een algemeen indexeringsprobleem in Adobe Commerce waarbij de index is vergrendeld door een ander proces en wordt overgeslagen.
exl-id: 542c714c-fad5-4f0e-9757-d90044c36bfc
feature: Catalog Management, Categories
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Index is vergrendeld door een ander proces

In dit artikel wordt gesproken over een algemeen indexeringsprobleem in Adobe Commerce waarbij de index is vergrendeld door een ander proces en wordt overgeslagen.

## Betrokken producten en versies

* Adobe Commerce 2.X

## Probleem

Tijdens een volledige herindex in uw CLI geeft Adobe Commerce u het foutbericht: *&#39;Index is vergrendeld door een ander herindexeringsproces. Overslaan.&#39;* Met andere woorden, wanneer het proces- of indextype vergrendeld is, kunt u dat bepaalde vergrendelde indextype niet opnieuw indexeren. De redex slaat altijd dat indextype over.

## Oorzaak

Deze fout kan optreden als de vorige index niet is voltooid. Enkele mogelijke redenen zijn:

* Het proces is onderbroken door een ander proces of een andere gebruiker.
* Geheugenlimiet.
* MySQL-fout, zoals een time-out.
* Fatale PHP fout tijdens de redex.

## Stappen om te reproduceren

1. Stel bijvoorbeeld dat de    ```bash    cataloginventory_stock ```    indextype is vergrendeld.
1. Wanneer u probeert alle gegevens opnieuw te indexeren door het CLI bevel in werking te stellen    ```bash    php bin/magento indexer:reindex    ``` krijgt u het volgende uitvoerresultaat:    ```bash    customer_grid index has been rebuilt successfully in 00:00:09    catalog_category_product index has been rebuilt successfully in 00:00:07    catalog_product_category index has been rebuilt successfully in 00:00:00    catalogrule_rule index has been rebuilt successfully in 00:00:05    catalog_product_attribute index has been rebuilt successfully in 00:00:04    cataloginventory_stock index is locked by another reindex process. Skipping.    catalog_product_price index has been rebuilt successfully in 00:00:01    catalogrule_product has been rebuilt successfully in 00:00:00    catalogsearch_fulltext index has been rebuilt successfully in 00:00:01    ```
1. Zoals u hierboven kunt zien,    ```bash    cataloginventory_stock```    indexproces is overgeslagen.


## Oplossing

U moet de indexstatus opnieuw instellen en vervolgens het nieuwe herindexproces uitvoeren. Voor de status van de reset-index moet u de opdracht uitvoeren:

```bash
bin/magento indexer:reset <index identifier>
```

Als u niet zeker weet wat de index-id&#39;s (code) zijn, kunt u deze weergeven met de opdracht:

```bash
bin/magento indexer:info
```

Voor de volledigheid zijn er alle mogelijke combinaties voor native indexen:

```bash
bin/magento indexer:reset design_config_grid;
bin/magento indexer:reset customer_grid;
bin/magento indexer:reset catalog_category_product;
bin/magento indexer:reset catalog_product_category;
bin/magento indexer:reset catalogrule_rule;
bin/magento indexer:reset catalog_product_attribute;
bin/magento indexer:reset cataloginventory_stock;
bin/magento indexer:reset catalog_product_price;
bin/magento indexer:reset catalogrule_product;
bin/magento indexer:reset catalogsearch_fulltext;
```


## Gerelateerde lezing

In onze kennisbasis voor ondersteuning:

* [Cron-taken vergrendelen taken van andere groepen (Adobe Commerce op cloudinfrastructuur)](/help/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.md)

In onze gebruikershandleiding:

* [ Beheer van de Index ](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/tools/index-management?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=reindexing)

In onze documentatie voor ontwikkelaars:

* [ Indexerend Overzicht ](https://developer.adobe.com/commerce/php/development/components/indexing/)
* [&#128279;](https://experienceleague.adobe.com/nl/docs/commerce-operations/performance-best-practices/configuration) de Beste praktijken van 0&rbrace; Indexers
* [ vorm en looppas uitsnede ](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs)
* [ beheer de indexen ](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/cli/manage-indexers)
* [ Optimalisering van de Indexer ](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/)
