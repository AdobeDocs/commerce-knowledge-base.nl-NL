---
title: Problemen met het hulpprogramma voor gegevensmigratie oplossen
description: Dit artikel biedt oplossingen voor fouten die kunnen optreden wanneer u het hulpprogramma voor gegevensmigratie uitvoert.
exl-id: 9beb31ae-ed3c-42e1-b0bf-33fb1c91e0ea
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# Problemen met het hulpprogramma voor gegevensmigratie oplossen

Dit artikel biedt oplossingen voor fouten die kunnen optreden wanneer u het hulpprogramma voor gegevensmigratie uitvoert.

## Brondocumenten/velden niet toegewezen {#source-documents-fields-not-mapped}

### Foutberichten

* ```bash    Source documents are not mapped: <EXTENSION_TABLE>    ```
* ```bash    Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <EXTENSION_FIELD>    ```

In zeldzame gevallen kan in het bericht worden vermeld

```bash
Destination documents
```

of

```bash
Destination fields
```

in plaats van bronbestanden.

### Oorzaak

Sommige Adobe Commerce versie 1-entiteiten (die in de meeste gevallen afkomstig zijn van extensies) bestaan niet in de Adobe Commerce versie 2-database.

Dit bericht verschijnt omdat het hulpmiddel van de Migratie van Gegevens interne tests in werking stelt om te verifiëren dat de lijsten en de gebieden tussen verenigbaar zijn *bron* (Adobe Commerce 1) en *doel* (Adobe Commerce 2).

### Mogelijke oplossingen

* De overeenkomstige Adobe Commerce 2-extensies installeren vanuit [Commerce Marketplace](https://marketplace.magento.com/).     Als de conflicterende gegevens afkomstig zijn van een extensie die eigen databasestructuurelementen toevoegt, kan de Adobe Commerce 2-versie van dezelfde extensie dergelijke elementen toevoegen aan de doeldatabase (Adobe Commerce 2) en zo de kwestie verhelpen.
* Gebruik de `-a` als u het gereedschap uitvoert om fouten automatisch op te lossen en te voorkomen dat de migratie stopt.
* Configureer het gereedschap om de problematische gegevens te negeren.

Als u database-entiteiten wilt negeren, voegt u de opdracht `<ignore>` tag toewijzen aan een entiteit in het dialoogvenster `map.xml` bestand, als volgt:

```xml
...
    <source>
        <document_rules>
            ...
            <!-- Ignore `sales_flat_invoice_grid` table -->
            <ignore>
                <document>sales_flat_invoice_grid</document>
            </ignore>
            <!-- Ignore `address_id` field of `sales_flat_order_address` table -->
            <ignore>
                <field>sales_flat_order_address.address_id</field>
            </ignore>
            ...
        </document_rules>
    </source>
    ...
```

>[!WARNING]
>
>Voordat u entiteiten negeert via een toewijzingsbestand of het `-a` wilt gebruiken, moet u ervoor zorgen dat u de desbetreffende gegevens niet in uw Adobe Commerce 2-winkel nodig hebt.

## Klasse wordt niet toegewezen in record {#class-does-not-exist-but-mentioned}

### Foutbericht

```bash
Class <extension/class_name> is not mapped in record <attribute_id=196>
```

### Oorzaak

Een klasse van Adobe Commerce 1-codebase is niet gevonden in Adobe Commerce 2-codebase tijdens de [EAV-migratiestap](https://devdocs.magento.com/guides/v2.3/migration/migration-tool-internal-spec.html#eav) in onze ontwikkelaarsdocumentatie. De ontbrekende klasse behoort meestal tot een [extension](https://glossary.magento.com/extension).

### Mogelijke oplossingen

* Installeer de overeenkomstige Adobe Commerce 2-extensie.
* Negeer het attribuut dat de kwestie veroorzaakt.    Voeg hiertoe het kenmerk toe aan de `ignore` in de `eav-attribute-groups.xml.dist` bestand.
* Klassetoewijzing toevoegen met de opdracht `class-map.xml.dist` bestand.

## Beperking externe sleutel mislukt

### Tekst van foutbericht

```bash
Foreign key <KEY_NAME> constraint fails on source database. Orphan records id: <id_1>, <id_2> from <child_table>.<field_id> has no referenced records in <parent_table>
```

### Oorzaak

Er ontbreken databaserecords in de `parent_table` waarbij de `field_id` van de `child_table` verwijst naar.

### Mogelijke oplossing

De records verwijderen uit het dialoogvenster `child_table` , als u ze niet nodig hebt.

Als u de records wilt bewaren, schakelt u het `Data Integrity Step` door de opties van het hulpprogramma voor gegevensmigratie te wijzigen `config.xml` .

## Duplicaten in herschreven URL

```xml
There are duplicates in URL rewrites:
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/10
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/12
```

### Oorzaak

De `Target path` in een URL moet rewrite door een uniek paar van `Request path` + `Store ID` . Deze fout rapporteert twee items die hetzelfde gebruiken `Request path` + `Store ID` paar met twee verschillende `Target path` waarden.

### Mogelijke oplossing

De optie `auto_resolve_urlrewrite_duplicates` in uw `config.xml` bestand.

Deze configuratie voegt een hash-string toe aan de conflicterende records van [URL](https://glossary.magento.com/url) herschrijft, en toont het resolutieresultaat in uw interface van de bevellijn.

## Entiteiten komen niet overeen {#mismatch-of-entities}

### Foutbericht

```bash
Mismatch of entities in the document: <DOCUMENT> Source: <COUNT_ITEMS_IN_SOURCE_TABLE> Destination: <COUNT_ITEMS_IN_DESTINATION_TABLE>
```

### Oorzaak

De fout treedt op tijdens de stap Volume controleren. Dit betekent dat het aantal records in de Adobe Commerce 2-database van het document niet hetzelfde is als in Adobe Commerce 1.

Ontbrekende records treden op wanneer een klant een bestelling plaatst tijdens de migratie.

### Mogelijke oplossing

Het hulpprogramma voor gegevensmigratie uitvoeren in `Delta` om incrementele wijzigingen over te brengen.

## Deltalog is niet geïnstalleerd {#deltalog-is-not-installed}

### Foutbericht

```bash
Deltalog for <TABLE_NAME> is not installed
```

### Oorzaak

Deze fout treedt op tijdens [incrementele migratie](https://devdocs.magento.com/guides/v2.3/migration/migration-migrate-delta.html) (in onze documentatie voor ontwikkelaars) van wijzigingen in gegevens. Dit betekent deltalogtabellen (met voorvoegsel) `m2_cl_*`) niet gevonden in de Adobe Commerce 1-database. Deze tabellen worden geïnstalleerd tijdens het gebruik van het gereedschap [gegevensmigratie](https://devdocs.magento.com/guides/v2.3/migration/migration-migrate-data.html) (in onze ontwikkelaarsdocumentatie) evenals gegevensbestandtrekkers die veranderingen volgen en lijstlijsten vullen.

Een reden voor de fout kan zijn dat u probeert te migreren van een *kopiëren* van je live Adobe Commerce 1-winkel, niet van de live winkel zelf. Wanneer u een kopie maakt van een live Adobe Commerce 1-winkel die nog nooit is gemigreerd, bevat de kopie niet de triggers en extra catalogustabellen die nodig zijn om een delta-migratie te voltooien, zodat de migratie mislukt. Het hulpmiddel van de Migratie van Gegevens maakt GEEN vergelijkingen tussen OB van AC1 en AC2 om de verschillen te migreren. In plaats daarvan gebruikt het gereedschap de triggers en de delta-tabellen die tijdens de eerste migratie zijn geïnstalleerd om volgende deltamigraties uit te voeren. In een dergelijk geval bevat uw exemplaar van de live Adobe Commerce 1 DB niet de triggers en overzichtstabellen die het hulpprogramma voor gegevensmigratie gebruikt om een migratie uit te voeren.

### Mogelijke oplossing

We raden u aan het migratieproces te testen vanuit een kopie van uw Adobe Commerce 1-database om uw migratieproblemen op te lossen. Nadat u de problemen in de kopie hebt opgelost, start u het migratieproces opnieuw vanuit uw livedatabank van Adobe Commerce 1. Dit zal helpen een vlot migratieproces verzekeren.
