---
title: Numerieke waarde van Adobe Commerce-database buiten bereik, "INT" tot "BIGINT"
description: Dit artikel biedt oplossingen als u een productupdate niet kunt opslaan, zoals een prijswijziging, of een product kunt verwijderen en dupliceren.
exl-id: e2a00371-9032-4e81-b60e-5456ba35be94
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Numerieke waarde Adobe Commerce-database valt buiten het bereik. `INT` tot `BIGINT`

>[!WARNING]
>
>Voordat de oplossing in dit artikel wordt geïmplementeerd (`INT` tot `BIGINT` schema update) de handelaren moeten altijd controleren dat het gebied zij gaan veranderen geen buitenlands-zeer belangrijke verhoudingen aan een andere lijst heeft. Als het veld geen externe-sleutelrelaties met een andere tabel heeft, zullen er problemen optreden omdat het verwante veld nog steeds `INT`. Zij kunnen de volgende vraag gebruiken om dit te verifiëren. Deze vraag maakt een lijst van de buitenlands-zeer belangrijke verhoudingen beschikbaar in het gegevensbestand voor het bepaalde lijstgebied:
>
```mysql
>SELECT 
>     TABLE_NAME,COLUMN_NAME,CONSTRAINT_NAME,REFERENCED_TABLE_NAME,REFERENCED_COLUMN_NAME
>FROM
>   INFORMATION_SCHEMA.KEY_COLUMN_USAGE
>WHERE
>     REFERENCED_TABLE_SCHEMA = '<database_name>' AND
>     REFERENCED_TABLE_NAME = '<table_name>' AND
>     REFERENCED_COLUMN_NAME = '<table_field>';
>```

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden) alle [ondersteunde versies](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

Dit artikel biedt oplossingen als u een productupdate niet kunt opslaan, zoals een prijswijziging, of een product kunt verwijderen en dupliceren.
Het foutbericht wordt mogelijk weergegeven *Het voorraadobject kan niet worden opgeslagen. Probeer het opnieuw.* Mogelijk kunt u niet implementeren na een productupdate. U kunt het volgende MySQL foutenbericht ook zien wanneer u in werking stelt `php bin/magento setup:upgrade` (In Adobe Commerce op cloudinfrastructuur wordt deze fout weergegeven in de implementatielogboeken):

```mysql
SQLSTATE[22003]: Numeric value out of range: 167 Out of range value for column 'value_id' at row 1, query was: INSERT INTO `catalog_product_entity_decimal` (`attribute_id`,`store_id`,`row_id`,`value`) VALUES (?, ?, ?, ?) ON DUPLICATE KEY UPDATE `attribute_id` = VALUES(`attribute_id`), `store_id` = VALUES(`store_id`), `row_id` = VALUES(`row_id`), `value` = VALUES(`value`)
```

De oplossingen die in het artikel worden beschreven zijn:
* Werk de `[ AUTO_INCREMENT ]` naar de volgende waarde in de tabel of
* `INT` tot `BIGINT` schema-update

Welke oplossing u gebruikt hangt van af wat de kwestie heeft veroorzaakt. Raadpleeg de onderstaande stappen om de oorzaak te isoleren.

## Stappen om de oorzaak te controleren


Controleer de hoogste waarde van de primaire sleutel door het volgende bevel in de terminal in werking te stellen: `SELECT MAX(value_id) FROM catalog_product_entity_int;`

Als de `max(value_id)` is lager dan de `max int(11) [ 4294967296 ]`en de `[ AUTO_INCREMENT ]` heeft een waarde groter dan of gelijk aan de `max int(11) [ 4294967296 ]`en vervolgens [het bijwerken van `[ AUTO_INCREMENT ]` naar de volgende waarde in de tabel](#update-the-auto-increment-to-the-next-value-from-the-table). Anders, overweeg a [`INT` tot `BIGINT` schema-update](#int_to_bigint_schema_update).

## Werk de `AUTO_INCREMENT` naar de volgende waarde in de tabel {#update-the-auto-increment-to-the-next-value-from-the-table}

>[!WARNING]
>
>Voer een gegevensbestandsteun uit alvorens de lijsten te veranderen. Plaats de site ook in [onderhoudsmodus](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode). Daarnaast wordt ook aangeraden de opdracht MYSQL optimaliseren uit te voeren in de databasetabellen (alleen naar tabellen waarin wijzigingen zijn aangebracht) nadat de wijzigingen zijn aangebracht.

>[!NOTE]
>
>De site moet in de onderhoudsmodus staan terwijl u de opdracht Optimaliseren voor specifieke tabellen uitvoert. Hierdoor worden tabellen volledig opnieuw samengesteld en wordt ruimte vrijgemaakt nadat gegevens uit tabellen zijn verwijderd.

Als de weergegeven waarde lager is dan `max int(11) [ 4294967296 ]` zoals getoond in het onderstaande voorbeeld eindoutput, dan een lijst `[ AUTO_INCREMENT ]` is gewijzigd in een getal dat groter of gelijk is aan de `max [ int(11) ]` waarde.

```mariadb
MariaDB [xxx]> SELECT MAX(value_id) FROM catalog_product_entity_int;
+---------------------+
| MAX(source_item_id) |
+---------------------+
|          4283174130 |
+---------------------+
```

Om te controleren of dit is voorgekomen, stel het volgende bevel in de terminal in werking:

```
MariaDB [xxx]> show create table catalog_product_entity_int;

...
) ENGINE=InnoDB AUTO_INCREMENT=4294967297 DEFAULT CHARSET=utf8 COMMENT='Catalog Product Integer Attribute Backend Table';
```

Zoals u in het bovenstaande voorbeeld kunt zien, voert u de tabel uit `[ AUTO_INCREMENT ]` is veranderd in een groter getal dan de `max int(11) [ 4294967296 ]`. De oplossing is het bijwerken van de `[ AUTO_INCREMENT]` naar de volgende waarde in de tabel:

```
ALTER TABLE catalog_product_entity_int AUTO_INCREMENT = 4283174131;
```

## `INT` tot `BIGINT` schema-update {#int_to_bigint_schema_update}

Als u echter de volgende query uitvoert `SELECT MAX(value_id) FROM catalog_product_entity_int;` de weergegeven waarde is hoger dan `max int(11) [ 4294967296 ]`  overwegen een `INT` tot `BIGINT` schema-update. Het datatype `BIGINT` heeft een groter waardebereik.

Daartoe:

1. Een aangepaste module maken in het dialoogvenster *app/code/* directory.
1. Maak in de aangepaste module een *db_schema.xml*. In *db_schema.xml* u zult datatype aan plaatsen `BIGINT`.
1. Voeg de volgende inhoud toe en voer vervolgens uit `bin/magento setup:upgrade` om bovenstaande wijzigingen toe te passen op de corresponderende tabel.

```
<?xml version="1.0"?>
<schema xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Setup/Declaration/Schema/etc/schema.xsd">
    <table name="catalog_product_entity_int">
        <column xsi:type="bigint" name="value_id" unsigned="false" nullable="false" identity="true"
                comment="Value ID"/>
    </table>
</schema>
```


## Gerelateerde lezing

* [Algemene MySQL-richtlijnen](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql.html) in de Commerce Installation Guide.
* [Uploaden database verliest verbinding met MySQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/database-upload-loses-connection-to-mysql.html) in onze kennisbasis voor ondersteuning.
* [Best practices voor databases voor Adobe Commerce op cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/database-best-practices-for-magento-commerce-cloud.html) in onze kennisbasis voor ondersteuning.
* [Meest voorkomende databaseproblemen in Adobe Commerce met cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/most-common-database-issues-in-magento-commerce-cloud.html) in onze kennisbasis voor ondersteuning.
