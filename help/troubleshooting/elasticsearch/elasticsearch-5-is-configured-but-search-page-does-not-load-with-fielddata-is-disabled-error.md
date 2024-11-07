---
title: Elasticsearch 5 is geconfigureerd, maar de zoekpagina wordt niet geladen met de fout "Veldgegevens is uitgeschakeld..."
description: 'Dit onderwerp beschrijft hoe te om de kwestie met Elasticsearch 5 te bevestigen, waar de onderzoekspagina niet laadt, en de uitzondering gelijkend op het volgende wordt geworpen:'
exl-id: f5fa8144-4e7c-45ce-89d0-a8367e91d6db
feature: Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Elasticsearch 5 is geconfigureerd, maar de zoekpagina wordt niet geladen met de fout &quot;Veldgegevens is uitgeschakeld...&quot;

Dit onderwerp beschrijft hoe te om de kwestie met Elasticsearch 5 te bevestigen, waar de onderzoekspagina niet laadt, en de uitzondering gelijkend op het volgende wordt geworpen:

```bash
{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}].
```

## Betrokken versies

* Adobe Commerce 2.2.x
* Elasticsearch v.5

>[!NOTE]
>
>Elasticsearch v.5 is vervangen voor Adobe Commerce 2.3.x

## Probleem

Voorwaarden: Elasticsearch 5 is geconfigureerd.

Op verzoek wordt de volgende uitzondering gegenereerd in logboeken:

```bash
{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}].
```

## Oorzaak

Standaard kunnen in Gelaagde navigatie alleen bepaalde typen productkenmerken worden gebruikt. Dit zijn Ja/Nee, Vervolgkeuzelijst, Vermenigvuldigen en Prijs. Dat is waarom in Commerce Admin, u geen attribuut van een ander type zoals **Gebruik in Gelaagde Navigatie** = *Filterable* of **Gebruik in Gelaagde Navigatie van de Resultaten van het Onderzoek** = *ja* kunt plaatsen. Maar er is een technische mogelijkheid om deze beperking te omzeilen door de `is_filterable` - en `is_filterable_in_search` -waarden in de database rechtstreeks te wijzigen. Als dit gebeurt en elk ander kenmerktype, zoals Datum, Tekst, enzovoort, is ingesteld voor gebruik in Gelaagde Navigatie, genereert Elasticsearch 5 een uitzondering.

Om ervoor te zorgen dat dit het geval is, moet u weten of er andere attributen behalve Dropdown, Multipleselect, en Prijs zijn, die worden geplaatst om in Gelaagde Navigatie te worden gebruikt. Voer de volgende query uit om naar deze kenmerken te zoeken:

```sql
SELECT ea.attribute_code, ea.frontend_input, cea.is_filterable, cea.is_filterable_in_search FROM eav_attribute AS ea
    -> INNER JOIN catalog_eav_attribute AS cea ON ea.attribute_id = cea.`attribute_id`
    -> WHERE (is_filterable = 1 OR is_filterable_in_search = 1) AND frontend_input NOT IN ('boolean', 'multiselect', 'select', 'price');
```

Het resultaat zal een lijst van attributen bevatten die voor Gelaagde Navigatie worden gebruikt, het waarvan type dit niet toestaat. Voer de in de volgende sectie beschreven stappen uit om dit te verhelpen.

## Oplossing

Als u het probleem wilt verhelpen, moet u `is_filterable` (dat wil zeggen gebruikt in gelaagde navigatie) en `filterable_in_search` (dat wil zeggen gebruikt in gelaagde navigatie in zoekresultaten) instellen op 0 (niet gebruikt). Voer hiertoe de volgende stappen uit:

1. Maak een back-up van de database.
1. Gebruik een gegevensbestandhulpmiddel zoals [ phpMyAdmin ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin), of toegang manueel OB van de bevellijn om de volgende SQL vraag in werking te stellen:

   ```sql
   UPDATE catalog_eav_attribute AS cea
       INNER JOIN eav_attribute AS ea
           ON ea.attribute_id = cea.attribute_id
   SET cea.is_filterable = 0, cea.is_filterable_in_search = 0
   WHERE (cea.is_filterable = 1 OR cea.is_filterable_in_search = 1)
       AND frontend_input NOT IN ('boolean', 'multiselect', 'select', 'price');
   ```

1. Voer de volledige herindex van Cataloguszoekopdrachten uit met de volgende opdracht:

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Cache opschonen door uit te voeren

   ```bash
   bin/magento cache:clean
   ```

of in Commerce Admin onder **Systeem** > **Hulpmiddelen** > **Beheer van het Geheime voorgeheugen**.

Nu moet u cataloguszoekopdrachten zonder problemen kunnen uitvoeren.
