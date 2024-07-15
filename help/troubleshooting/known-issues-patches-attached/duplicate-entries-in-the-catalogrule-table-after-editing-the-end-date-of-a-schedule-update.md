---
title: Items in de catalogustabel dupliceren na het bewerken van de einddatum van een planningupdate
description: Dit artikel verstrekt een flard voor de bekende kwestie van Adobe Commerce 2.2.3 waar het uitgeven van de einddatum of de tijd van een de programmaupdate van de catalogusprijs in het toevoegen van dubbele ingangen aan de lijst ` catalogrule` en fouten in ` catalogrule_rule ` (de regelproduct van de Catalogus) indexer herdex resulteert.
exl-id: e900b712-d0f5-4404-8441-64522035ce44
feature: Cache, Catalog Management, Marketing Tools
role: Developer
source-git-commit: 496151d1fe29a66d84349e4a96e7c5563a92c5c4
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Items in de catalogustabel dupliceren na het bewerken van de einddatum van een planningupdate

Dit artikel bevat een patch voor de bekende Adobe Commerce 2.2.3-uitgave, waarbij het bewerken van de einddatum of tijd van een update van een catalogusprijsregel leidt tot het toevoegen van dubbele vermeldingen aan de `catalogrule` -tabel en fouten in de indexeerindex van `catalogrule_rule` (het catalogusregelproduct).

## Probleem

Wanneer u de einddatum of tijd wijzigt van een bestaande update van de catalogusprijsregel, worden dubbele vermeldingen gemaakt in de databasetabel van `catalogrule` . Dientengevolge, ontbreekt de `catalogrule_rule` herdex met de volgende fout in het uitzonderingslogboek: *Punt met zelfde identiteitskaart bestaat reeds*.

<u> Stappen om </u> te reproduceren:

Eerste vereisten: De `catalogrule_rule` indexeerder wordt geplaatst aan *[Update op Programma ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html)* wijze.

1. In Commerce Admin, creeer een nieuwe Regel van de Prijs van de Catalogus onder **Marketing** > **Bevorderingen** > **Regel van de Prijs van de Catalogus**.
1. In het **net van de Regel van de Prijs van de Catalogus**, klik **uitgeven**, en programma een nieuwe Update en plaats **Status** aan *Actief.*
1. Klik **Mening/geef uit** naast de pas gecreëerde Update en verander de einddatum in een vroegere tijd.
1. Sla de update op.
1. Voer de opdracht voor opnieuw indexeren uit voor de `catalogrule_rule` -index.

<u> Verwacht resultaat </u>:

De index van `catalogrule_rule` is opnieuw geïndexeerd. Geen dubbele vermeldingen in de `catalogrule` -tabel.

<u> Werkelijk resultaat </u>:

Opnieuw indexeren ontbreekt met de volgende fout: *Punt met zelfde identiteitskaart bestaat reeds*, omdat er dubbele ingangen in de `catalogrule` lijst zijn.

## Oplossing

U kunt dit probleem oplossen door de bijgevoegde patch toe te passen en de bestaande dubbele vermeldingen te verwijderen. Zie [ verwijder gedupliceerde ingangen ](#remove) sectie voor details over het controleren als de duplicaten bestaan en hen verwijderen.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[MDVA-10974\_EE\_2.2.3\_COMPOSER\_v2.patch downloaden](assets/MDVA-10974_EE_2.2.3_COMPOSER_v2.patch.zip)

### Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce 2.2.3

De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce over cloudinfrastructuur 2.2.1 - 2.2.5
* Adobe Commerce op locatie 2.2.1 - 2.2.2 en 2.2.4 - 2.2.5

## Hoe de pleister aanbrengen

Zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies in onze basis van de steunkennis wordt verstrekt.

## Gedupliceerde items verwijderen {#remove}

>[!NOTE]
>
>Zorg ervoor dat u een recente back-up hebt voordat u wijzigingen aanbrengt.

Ga als volgt te werk om de gedupliceerde items te zoeken en te verwijderen:

1. Voer de volgende query uit om te controleren of de gedupliceerde items in de database aanwezig zijn:

   ```SQL
   SELECT entity_id, "catalog_product_entity" AS entity_table FROM catalog_product_entity GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT entity_id, "catalog_product_entity" AS entity_table FROM catalog_product_entity group by entity_id, updated_in having count(*) > 1    UNION    SELECT rule_id as entity_id, "catalogrule" AS entity_table FROM catalogrule GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "catalogrule" AS entity_table FROM catalogrule GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "salesrule" AS entity_table FROM salesrule GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT rule_id as entity_id, "salesrule" AS entity_table FROM salesrule GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT page_id as entity_id, "cms_page" AS entity_table FROM cms_page GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT page_id as entity_id, "cms_page" AS entity_table FROM cms_page GROUP BY entity_id, updated_in HAVING COUNT(*) > 1    UNION    SELECT block_id as entity_id, "cms_block" AS entity_table FROM cms_block GROUP BY entity_id, created_in HAVING COUNT(*) > 1    UNION    SELECT block_id as entity_id, "cms_block" AS entity_table FROM cms_block GROUP BY entity_id, updated_in HAVING COUNT(*) > 1;
   ```

   Als er geen dubbele ingangen zijn, zal de reactie leeg zijn en u moet niets anders doen. Als de gedupliceerde items bestaan, krijgt u de tabelnaam en `entity_id` van de gedupliceerde entiteit, zoals in het volgende voorbeeld:

   ![ table_results1.png ](assets/table_results1.png)

   Houd er rekening mee dat in bepaalde tabellen de naam van het veld met de id van de entiteit anders zal zijn dan in `entity_id` . In de tabel `cms_page` zou dit bijvoorbeeld `page_id` in plaats van `entity_id` zijn.

1. Vervolgens moet u de duplicaten nader bekijken en begrijpen welke gegevens moeten worden verwijderd. Gebruik een query die lijkt op de volgende om de duplicaten te zien. Vervang de tabelnaam, de id-naam en de waarde van de entiteit op basis van de resultaten die u in de vorige stap hebt ontvangen.

   ```sql
   SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
   ```

   U ontvangt een lijst met records met meerdere kolommen. Voorbeeld:

   ![ table_results2.png ](assets/table_results2.png)

   De waarden `created_in` en `updated_in` moeten dit patroon volgen: de waarde `created_in` van de huidige rij is gelijk aan de waarde `updated_in` in de vorige rij. Ook, zou de **eerste rij** moeten bevatten creeerde \_in = 1 en de **laatste rij** zou moeten bijgewerkt \_in = 2147483647 bevatten. (Als er slechts 1 rij is, moet u creeerde \_in=1 **zien en** bijgewerkt \_in=2147483647). De rij(en) waarvoor dit patroon is afgebroken, moet(en) worden geschrapt. In ons voorbeeld zou dit de rij zijn met `row_id` =2052 aangezien de tweede en derde rij beide dezelfde waarde hebben voor created_in: 1540837826, wat niet zou moeten voorkomen.

1. Verwijder het duplicaat met behulp van een query die lijkt op de volgende. Vervang de tabelnaam, de id-naam en de waarde van de entiteit op basis van de resultaten die u in de vorige stappen hebt ontvangen:

   ```sql
   DELETE FROM catalog_product_entity WHERE entity_id = 483 AND row_id = 2052;
   ```

1. Cache opschonen door uit te voeren:

   ```bash
   bin/magento cache:clean
   ```

   of in Commerce Admin onder **Systeem** > **Hulpmiddelen** > **Beheer van het Geheime voorgeheugen**.

## Nuttige koppelingen in de documentatie voor ontwikkelaars

* [ pas douaneflarden op Adobe Commerce op wolkeninfrastructuur toe ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)
* [ Mening en beheer logboeken voor Adobe Commerce op wolkeninfrastructuur ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html))

## Bijgevoegde bestanden
