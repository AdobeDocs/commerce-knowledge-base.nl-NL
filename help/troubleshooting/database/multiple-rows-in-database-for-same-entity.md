---
title: Database bevat meerdere rijen voor dezelfde entiteit
description: Dit artikel biedt een oplossing voor het probleem waarbij er meerdere rijen voor dezelfde entiteitsidentiteitskaart in de database zijn.
feature: Catalog Management, Categories, Services, Storefront
role: Developer
exl-id: 09d5c321-9c45-4041-b6f6-831efca0977e
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# Meerdere rijen in de database voor dezelfde entiteit

Dit artikel biedt een oplossing voor het probleem waarbij er meerdere rijen voor dezelfde entiteitsidentiteitskaart in de database zijn.

## Betrokken producten en versies:

* Adobe Commerce (alle versies)

## Probleem

De database bevat meerdere rijen voor dezelfde entiteit-id.

Bijvoorbeeld, na het ontvangen van een lijst van verslagen met dubbele entiteit IDs wanneer u deze vraag in werking stelt:

```
SELECT * FROM $entityTable WHERE $column = <$entityID> ORDER BY created_in;
```

Waarbij `$entityID = ID` van de pagina Categorie/product/winkelprijsegel/catalogusprijsregel/CMS.

| Entiteit | $entityTable | $column |
|------------------|-----------------------------------|------------------|
| Categorie/Product | catalog_category_entiteit/catalog_product_entiteit | entity_id |
| Prijsregel winkelwagentje/regel catalogusprijs | winkelregel/catalogusregel | rule_id |
| CMS-pagina | cms_page | page_id |

## Oorzaak

Dit is het verwachte gedrag. De meerdere rijen worden gemaakt door de functie voor het opslaan van inhoud:

* Als u een begindatum zonder een einddatum opgeeft, zijn er minstens twee rijen met dezelfde entiteit-/regel-/pagina-id. Één rij zal op de originele staat van de entiteit (de rij wijzen waarin `created_in=1`), en één rij zal op het *Eind van de Geplande Update* wijzen.

* Als u een begindatum opgeeft met een einddatum, zijn er ten minste drie rijen met dezelfde entiteit-/regel-/pagina-id. Één rij zal op de originele staat van de entiteit (de rij waarin `created_in=1`) wijzen, zal één rij voor het *Begin van de Geplande Update* zijn, en één rij zal voor het *Eind van de Geplande Update* zijn.

In deze query ziet u bijvoorbeeld:

```
SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
```

![ multiple_rows_in_database.png ](assets/multiple_rows_in_database.png)

* De waarden `created_in` en `updated_in` moeten dit patroon volgen: de waarde `created_in` van de huidige rij is gelijk aan de waarde `updated_in` in de vorige rij. Bovendien moet de eerste rij `created_in = 1` bevatten en de laatste rij `updated_in = 2147483647` . (Als er slechts één rij is, moet u `created_in=1` en `updated_in=2147483647` zien.)

### Waarom wordt de tweede DB-vermelding (en alle volgende vermeldingen) in de DB voor dezelfde entiteit weergegeven?

* De tweede DB-record (en mogelijk de volgende record) voor de betrokken entiteit betekent dat er updates voor het opslaan van inhoud zijn gepland met de module `Magento_Staging` , die een extra record maakt voor een entiteit in de respectievelijke tabellen.

Er treedt alleen een probleem op als de records dezelfde waarden hebben voor de kolommen `created_in` of `updated_in` .

## Oplossing

Dit is het verwachte gedrag en leidt alleen tot problemen als er verschillen tussen de rijen zijn.

## Gerelateerde lezing

* [ de Veranderingen in categorieën worden niet bewaard ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/changes-to-categories-are-not-being-saved.html?lang=nl-NL) in onze basis van de steunkennis
* [ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/nl/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
