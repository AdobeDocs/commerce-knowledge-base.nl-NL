---
title: Index is vergrendeld door een ander proces
description: In dit artikel wordt gesproken over een algemeen indexeringsprobleem in Adobe Commerce waarbij de index is vergrendeld door een ander proces en wordt overgeslagen.
exl-id: 542c714c-fad5-4f0e-9757-d90044c36bfc
feature: Catalog Management, Categories
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Index is vergrendeld door een ander proces

In dit artikel wordt gesproken over een algemeen indexeringsprobleem in Adobe Commerce waarbij de index is vergrendeld door een ander proces en wordt overgeslagen.

## Betrokken producten en versies

* Adobe Commerce 2.X

## Probleem

Tijdens een volledige redex in uw CLI, geeft Adobe Commerce u het foutenbericht: *&#39;Index is vergrendeld door een ander herindexeringsproces. Overslaan.&#39;* Met andere woorden, wanneer het proces of het indextype vergrendeld is, kunt u dat bepaalde vergrendelde indextype niet opnieuw indexeren. De redex slaat altijd dat indextype over.

## Oorzaak

Deze fout kan optreden als de vorige index niet is voltooid. Enkele mogelijke redenen zijn:

* Het proces is onderbroken door een ander proces of een andere gebruiker.
* Geheugenlimiet.
* MySQL-fout, zoals een time-out.
* Fatale PHP fout tijdens de redex.

## Stappen om te reproduceren

1. Stel bijvoorbeeld dat de    ```bash    cataloginventory_stock ```    indextype is vergrendeld.
1. Wanneer u probeert alle gegevens opnieuw te indexeren door het CLI bevel in werking te stellen    ```bash    php bin/magento indexer:reindex    ```krijgt u het volgende uitvoerresultaat:    ```bash    customer_grid index has been rebuilt successfully in 00:00:09    catalog_category_product index has been rebuilt successfully in 00:00:07    catalog_product_category index has been rebuilt successfully in 00:00:00    catalogrule_rule index has been rebuilt successfully in 00:00:05    catalog_product_attribute index has been rebuilt successfully in 00:00:04    cataloginventory_stock index is locked by another reindex process. Skipping.    catalog_product_price index has been rebuilt successfully in 00:00:01    catalogrule_product has been rebuilt successfully in 00:00:00    catalogsearch_fulltext index has been rebuilt successfully in 00:00:01    ```
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

* [Indexbeheer](https://docs.magento.com/user-guide/system/index-management.html?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=reindexing)

In onze documentatie voor ontwikkelaars:

* [Overzicht van indexering](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html)
* [Aanbevolen werkwijzen voor indexen](https://devdocs.magento.com/guides/v2.3/performance-best-practices/configuration.html#indexers)
* [Uitsnede configureren en uitvoeren](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cron.html)
* [De indexen beheren](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html)
* [Indexeroptimalisatie](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexer-batch.html)
