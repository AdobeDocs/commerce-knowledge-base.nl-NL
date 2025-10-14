---
title: Problemen met het hulpprogramma voor gegevensmigratie oplossen
description: Dit artikel biedt oplossingen voor fouten die kunnen optreden wanneer u het hulpprogramma voor gegevensmigratie uitvoert.
exl-id: 9beb31ae-ed3c-42e1-b0bf-33fb1c91e0ea
feature: Data Import/Export
role: Developer
source-git-commit: 958067830d32b1f10ffa669307ec76d1e14b82a4
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Problemen met het hulpprogramma voor gegevensmigratie oplossen

Dit artikel biedt oplossingen voor fouten die kunnen optreden wanneer u het hulpprogramma voor gegevensmigratie uitvoert.

## Source-documenten/velden niet toegewezen {#source-documents-fields-not-mapped}

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

Dit bericht verschijnt omdat het Hulpmiddel van de Migratie van Gegevens interne tests in werking stelt om te verifiëren dat de lijsten en de gebieden tussen *bron* (Adobe Commerce 1) en *bestemmings* (Adobe Commerce 2) gegevensbestanden verenigbaar zijn.

### Mogelijke oplossingen

* Installeer de overeenkomstige Adobe Commerce 2 uitbreidingen van [&#x200B; Commerce Marketplace &#x200B;](https://marketplace.magento.com/).     Als de conflicterende gegevens afkomstig zijn van een extensie die eigen databasestructuurelementen toevoegt, kan de Adobe Commerce 2-versie van dezelfde extensie dergelijke elementen toevoegen aan de doeldatabase (Adobe Commerce 2) en zo de kwestie verhelpen.
* Gebruik het argument `-a` wanneer u het gereedschap uitvoert om fouten automatisch op te lossen en te voorkomen dat de migratie stopt.
* Configureer het gereedschap om de problematische gegevens te negeren.

Als u database-entiteiten wilt negeren, voegt u de tag `<ignore>` als volgt toe aan een entiteit in het `map.xml` -bestand:

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
>Voordat u entiteiten via een toewijzingsbestand of de optie `-a` negeert, moet u ervoor zorgen dat u de desbetreffende gegevens niet nodig hebt in uw Adobe Commerce 2-winkel.

## Klasse wordt niet toegewezen in record {#class-does-not-exist-but-mentioned}

### Foutbericht

```bash
Class <extension/class_name> is not mapped in record <attribute_id=196>
```

### Oorzaak

Een klasse van Adobe Commerce 1 codebase kon niet in Adobe Commerce 2 codebase tijdens de [&#x200B; EAV migratiestap &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/data-migration/basics/technical-specification) in onze ontwikkelaarsdocumentatie worden gevonden. In de meeste gevallen, behoort de ontbrekende klasse tot een [&#x200B; uitbreiding &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/implementation-playbook/glossary#extension).

### Mogelijke oplossingen

* Installeer de overeenkomstige Adobe Commerce 2-extensie.
* Negeer het attribuut dat de kwestie veroorzaakt.    Voeg hiertoe het kenmerk toe aan de groep `ignore` in het `eav-attribute-groups.xml.dist` -bestand.
* Voeg klassentoewijzing toe met behulp van het `class-map.xml.dist` -bestand.

## Beperking externe sleutel mislukt

### Tekst van foutbericht

```bash
Foreign key <KEY_NAME> constraint fails on source database. Orphan records id: <id_1>, <id_2> from <child_table>.<field_id> has no referenced records in <parent_table>
```

### Oorzaak

Er ontbreken databaserecords in de `parent_table` waarnaar de `field_id` van de `child_table` verwijst.

### Mogelijke oplossing

Verwijder de records uit de `child_table` als u ze niet nodig hebt.

Als u de records wilt bewaren, schakelt u de `Data Integrity Step` uit door de functies `config.xml` van het gereedschap Gegevensmigratie te wijzigen.

## Duplicaten in herschreven URL

```xml
There are duplicates in URL rewrites:
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/10
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/12
```

### Oorzaak

De waarde `Target path` in een URL voor herschrijven moet worden opgegeven met een uniek paar `Request path` + `Store ID` . Deze fout rapporteert twee items die hetzelfde `Request path` + `Store ID` -paar gebruiken met twee verschillende `Target path` -waarden.

### Mogelijke oplossing

Schakel de optie `auto_resolve_urlrewrite_duplicates` in het `config.xml` -bestand in.

Deze configuratie voegt een knoeiboel-koord aan de conflicterende verslagen van URL toe herschrijft, en toont het resolutieresultaat in uw interface van de bevellijn.

## Entiteiten komen niet overeen {#mismatch-of-entities}

### Foutbericht

```bash
Mismatch of entities in the document: <DOCUMENT> Source: <COUNT_ITEMS_IN_SOURCE_TABLE> Destination: <COUNT_ITEMS_IN_DESTINATION_TABLE>
```

### Oorzaak

De fout treedt op tijdens de stap Volume controleren. Dit betekent dat het aantal records in de Adobe Commerce 2-database van het document niet hetzelfde is als in Adobe Commerce 1.

Ontbrekende records treden op wanneer een klant een bestelling plaatst tijdens de migratie.

### Mogelijke oplossing

Voer het gereedschap Gegevensmigratie uit in de modus `Delta` om incrementele wijzigingen over te brengen.

## Deltalog is niet geïnstalleerd {#deltalog-is-not-installed}

### Foutbericht

```bash
Deltalog for <TABLE_NAME> is not installed
```

### Oorzaak

Deze fout komt tijdens [&#x200B; stijgende migratie &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/data-migration/migrate-data/delta) (in onze ontwikkelaarsdocumentatie) van veranderingen in gegevens voor. Dit betekent dat er geen Deltalog-tabellen (met voorvoegsel `m2_cl_*` ) zijn gevonden in de Adobe Commerce 1-database. Het hulpmiddel installeert deze lijsten tijdens [&#x200B; gegevensmigratie &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/data-migration/migrate-data/data) (in onze ontwikkelaarsdocumentatie) evenals gegevensbestandtrekkers die veranderingen volgen en lijstlijsten vullen.

Één reden voor de fout zou kunnen zijn dat u probeert om van a *exemplaar* van uw levende Adobe Commerce 1 opslag, niet van de levende opslag zelf te migreren. Wanneer u een kopie maakt van een live Adobe Commerce 1-winkel die nog nooit is gemigreerd, bevat de kopie niet de triggers en extra catalogustabellen die nodig zijn om een delta-migratie te voltooien, zodat de migratie mislukt. Het hulpmiddel van de Migratie van Gegevens maakt GEEN vergelijkingen tussen OB van AC1 en AC2 om de verschillen te migreren. In plaats daarvan gebruikt het gereedschap de triggers en de delta-tabellen die tijdens de eerste migratie zijn geïnstalleerd om volgende deltamigraties uit te voeren. In een dergelijk geval bevat uw exemplaar van de live Adobe Commerce 1 DB niet de triggers en overzichtstabellen die het hulpprogramma voor gegevensmigratie gebruikt om een migratie uit te voeren.

### Mogelijke oplossing

We raden u aan het migratieproces te testen vanuit een kopie van uw Adobe Commerce 1-database om uw migratieproblemen op te lossen. Nadat u de problemen in de kopie hebt opgelost, start u het migratieproces opnieuw vanuit uw livedatabank van Adobe Commerce 1. Dit zal helpen een vlot migratieproces verzekeren.

## Gerelateerde lezing

[&#x200B; Beste praktijken voor het wijzigen van gegevensbestandlijsten &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce

