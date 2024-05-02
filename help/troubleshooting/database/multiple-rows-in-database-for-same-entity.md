---
title: Database bevat meerdere rijen voor dezelfde entiteit
description: Dit artikel biedt een oplossing voor het probleem waarbij er meerdere rijen voor dezelfde entiteitsidentiteitskaart in de database zijn.
feature: Catalog Management, Categories, Services, Storefront
role: Developer
exl-id: 09d5c321-9c45-4041-b6f6-831efca0977e
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '432'
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

Wanneer `$entityID = ID` van categorie/product/winkelprijsegel/catalogusprijsregel/CMS-pagina.

| Entiteit | $entityTable | $column |
|------------------|-----------------------------------|------------------|
| Categorie/Product | catalog_category_entiteit/catalog_product_entiteit | entity_id |
| Prijsregel winkelwagentje/regel catalogusprijs | winkelregel/catalogusregel | rule_id |
| CMS-pagina | cms_page | page_id |

## Oorzaak

Dit is het verwachte gedrag. De meerdere rijen worden gemaakt door de functie voor het opslaan van inhoud:

* Als u een begindatum zonder een einddatum opgeeft, zijn er minstens twee rijen met dezelfde entiteit-/regel-/pagina-id. Eén rij geeft de oorspronkelijke staat van de entiteit aan (de rij waarin `created_in=1`), en één rij geeft de *Einde van de geplande update*.

* Als u een begindatum opgeeft met een einddatum, zijn er ten minste drie rijen met dezelfde entiteit-/regel-/pagina-id. Eén rij geeft de oorspronkelijke staat van de entiteit aan (de rij waarin `created_in=1`), is er één rij voor de *Begin van de geplande update* en één rij voor de *Einde van de geplande update*.

In deze query ziet u bijvoorbeeld:

```
SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
```

![multiple_rows_in_database.png](assets/multiple_rows_in_database.png)

* De `created_in` en `updated_in` De waarden moeten dit patroon volgen: De `created_in` waarde van de huidige rij is gelijk aan de waarde van `updated_in` waarde in de vorige rij. De eerste rij moet ook `created_in = 1` en de laatste rij bevat `updated_in = 2147483647`. (Als er slechts één rij is, moet u zien `created_in=1` en `updated_in=2147483647`).

### Waarom wordt de tweede DB-vermelding (en alle volgende vermeldingen) in de DB voor dezelfde entiteit weergegeven?

* De tweede DB-record (en eventueel de volgende record) voor de betrokken entiteit betekent dat er updates voor het opslaan van inhoud zijn gepland met behulp van de `Magento_Staging` die een extra record voor een entiteit in de desbetreffende tabellen oplevert.

Er zou alleen een probleem optreden als de records dezelfde waarden voor de `created_in` of `updated_in` kolommen.

## Oplossing

Dit is het verwachte gedrag en leidt alleen tot problemen als er verschillen tussen de rijen zijn.

## Gerelateerde lezing

* [Wijzigingen in categorieën worden niet opgeslagen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/changes-to-categories-are-not-being-saved.html) in onze kennisbasis voor ondersteuning.
* [Items in de catalogustabel dupliceren na het bewerken van de einddatum van een planningupdate](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/duplicate-entries-in-the-catalogrule-table-after-editing-the-end-date-of-a-schedule-update.html) in onze kennisbasis voor ondersteuning.
