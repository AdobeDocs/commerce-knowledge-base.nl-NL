---
title: Numerieke waarde van Adobe Commerce-database buiten bereik, "INT" tot "BIGINT"
description: Dit artikel biedt oplossingen als u een productupdate niet kunt opslaan, zoals een prijswijziging, of een product kunt verwijderen en dupliceren.
exl-id: e2a00371-9032-4e81-b60e-5456ba35be94
feature: Services
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# Numerieke waarde Adobe Commerce-database buiten bereik, `INT` tot `BIGINT`

>[!WARNING]
>
>Voordat de oplossing in dit artikel wordt geïmplementeerd (`INT` tot `BIGINT` schema-update), moeten handelaren altijd controleren of het veld dat zij gaan wijzigen GEEN relaties met een andere tabel met een externe sleutel heeft. Als het veld geen relaties met externe sleutels heeft met een andere tabel, zullen er problemen optreden omdat het verwante veld nog steeds `INT` is. Zij kunnen de volgende vraag gebruiken om dit te verifiëren. Deze vraag maakt een lijst van de buitenlands-zeer belangrijke verhoudingen beschikbaar in het gegevensbestand voor het bepaalde lijstgebied:
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

* Adobe Commerce (alle plaatsingsmethodes) alle [ gesteunde versies ](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

Dit artikel biedt oplossingen als u een productupdate niet kunt opslaan, zoals een prijswijziging, of een product kunt verwijderen en dupliceren.
U kunt het foutenbericht *zien het voorraadpunt kon niet worden bewaard. Probeer het opnieuw.* Mogelijk kunt u niet implementeren na een productupdate. Het volgende [!DNL MySQL] foutbericht wordt ook weergegeven wanneer u `php bin/magento setup:upgrade` uitvoert (in Adobe Commerce op de cloud-infrastructuur wordt deze fout weergegeven in de implementatielogboeken):

```mysql
SQLSTATE[22003]: Numeric value out of range: 167 Out of range value for column 'value_id' at row 1, query was: INSERT INTO `catalog_product_entity_decimal` (`attribute_id`,`store_id`,`row_id`,`value`) VALUES (?, ?, ?, ?) ON DUPLICATE KEY UPDATE `attribute_id` = VALUES(`attribute_id`), `store_id` = VALUES(`store_id`), `row_id` = VALUES(`row_id`), `value` = VALUES(`value`)
```

De oplossingen die in het artikel worden beschreven zijn:
* Werk de `[ AUTO_INCREMENT ]` bij naar de volgende waarde in de tabel of
* `INT` naar `BIGINT` schema-update

Welke oplossing u gebruikt hangt van af wat de kwestie heeft veroorzaakt. Raadpleeg de onderstaande stappen om de oorzaak te isoleren.

## Stappen om de oorzaak te controleren


Controleer de hoogste waarde van de primaire sleutel door de volgende opdracht in de terminal uit te voeren: `SELECT MAX(value_id) FROM catalog_product_entity_int;`

Als `max(value_id)` lager is dan `max int(11) [ 4294967296 ]`, en `[ AUTO_INCREMENT ]` een waarde groter dan of gelijk aan `max int(11) [ 4294967296 ]` heeft, dan denk na [ bijwerkt `[ AUTO_INCREMENT ]` aan de volgende waarde van de lijst ](#update-the-auto-increment-to-the-next-value-from-the-table). Anders, overweeg a [`INT` aan `BIGINT` schemaupdate ](#int_to_bigint_schema_update).

## De `AUTO_INCREMENT` bijwerken naar de volgende waarde in de tabel {#update-the-auto-increment-to-the-next-value-from-the-table}

>[!WARNING]
>
>Voer een gegevensbestandsteun uit alvorens de lijsten te veranderen. Ook, zet de plaats in [ onderhoudswijze ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode). Daarnaast wordt ook aangeraden de opdracht [!DNL MySQL] optimaliseren uit te voeren in de databasetabellen (alleen naar tabellen waarin wijzigingen zijn aangebracht) nadat de wijzigingen zijn aangebracht.

>[!NOTE]
>
>De site moet in de onderhoudsmodus staan terwijl u de opdracht Optimaliseren voor specifieke tabellen uitvoert. Hierdoor worden tabellen volledig opnieuw samengesteld en wordt ruimte vrijgemaakt nadat gegevens uit tabellen zijn verwijderd.

Als de getoonde waarde lager is dan `max int(11) [ 4294967296 ]`, zoals in het onderstaande voorbeeld wordt getoond, is de einduitvoer van een tabel `[ AUTO_INCREMENT ]` gewijzigd in een getal dat groter of gelijk is aan de `max [ int(11) ]` -waarde.

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

Zoals u in het bovenstaande voorbeeld kunt zien, is de tabel `[ AUTO_INCREMENT ]` gewijzigd in een groter getal dan de `max int(11) [ 4294967296 ]` . U kunt de `[ AUTO_INCREMENT]` bijwerken naar de volgende waarde in de tabel:

```
ALTER TABLE catalog_product_entity_int AUTO_INCREMENT = 4283174131;
```

## `INT` naar `BIGINT` schema-update {#int_to_bigint_schema_update}

Als de volgende query `SELECT MAX(value_id) FROM catalog_product_entity_int;` wordt uitgevoerd, is de weergegeven waarde echter hoger dan `max int(11) [ 4294967296 ]` u kunt overwegen een schema-update `INT` uit te voeren naar `BIGINT` . Het datatype `BIGINT` heeft een groter waardenbereik.

Daartoe:

1. Creeer een douanemodule binnen de *app/code/* folder.
1. In de douanemodule creeert a *db_schema.xml*. In *db_schema.xml* zult u datatype aan `BIGINT` plaatsen.
1. Voeg de volgende inhoud toe en voer vervolgens `bin/magento setup:upgrade` uit om de bovenstaande wijzigingen toe te passen op de corresponderende tabel.

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

* [ Algemene  [!DNL MySQL]  richtlijnen ](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql.html) in de Gids van de Installatie van Commerce
* [ uploadt het Gegevensbestand verliest verbinding aan  [!DNL MySQL] ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/database-upload-loses-connection-to-mysql.html) in onze basis van de steunkennis
* [ beste praktijken van het Gegevensbestand voor Adobe Commerce op wolkeninfrastructuur ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/database-best-practices-for-magento-commerce-cloud.html) in onze basis van de steunkennis
* [ gemeenschappelijkste gegevensbestandkwesties in Adobe Commerce op wolkeninfrastructuur ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/most-common-database-issues-in-magento-commerce-cloud.html) in onze basis van de steunkennis
* [ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
