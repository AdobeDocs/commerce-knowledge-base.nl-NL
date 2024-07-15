---
title: Live zoekcatalogus is niet gesynchroniseerd
description: Dit artikel biedt oplossingen voor het Adobe Commerce-probleem waarbij de catalogusgegevens niet correct zijn gesynchroniseerd wanneer u de extensie Live zoeken gebruikt.
exl-id: cd2e602f-b2c7-4ecf-874f-ec5f99ae1900
feature: Catalog Management, Search
role: Developer
source-git-commit: a1b049dab989d5d8594d86b64b778e6e277a9f41
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 0%

---

# Live zoekcatalogus is niet gesynchroniseerd

Dit artikel biedt oplossingen voor het Adobe Commerce-probleem waarbij de catalogusgegevens niet correct zijn gesynchroniseerd wanneer u de extensie Live zoeken gebruikt.

## Betrokken producten en versies

* Adobe Commerce 2.4.x met Live Search-extensie geïnstalleerd

## Probleem

De catalogusgegevens worden niet correct gesynchroniseerd of er is een nieuw product toegevoegd, maar dit wordt niet weergegeven in de zoekresultaten.

<u> Stappen om te reproduceren </u>

1. Vorm en verbind Levende Onderzoek voor uw instantie van Adobe Commerce zoals die in [ wordt beschreven installeer Levende Onderzoek > vormen API sleutels ](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#configure-api-keys) in onze gebruikersdocumentatie.
1. Na 30 minuten, verifieer de uitgevoerde catalogusgegevens zoals die in [ worden beschreven installeer Levende Onderzoek > verifieer de uitvoer ](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#verify-export) in onze gebruikersdocumentatie.
1. Na 30 minuten, test de verbinding zoals die in [ wordt beschreven installeer Levende Onderzoek > test de verbinding ](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#test-connection) in onze gebruikersdocumentatie.

of

1. Voeg een nieuw product toe aan de catalogus.
1. Probeer een zoekquery uit te voeren met de productnaam of andere doorzoekbare kenmerken na 15-20 minuten van de tijd dat Magento indexer + cron zijn uitgevoerd om gegevens te synchroniseren naar back-endservice.

<u> Verwacht resultaat </u>

* Geëxporteerde catalogusgegevens kunnen worden geverifieerd
* Verbinding is gelukt
* Nieuw product wordt weergegeven in zoekresultaten.

<u> Werkelijk resultaat </u>

De geëxporteerde catalogus kan niet worden geverifieerd en/of de verbinding is niet tot stand gebracht omdat de API-sleutel is gewijzigd.

## Oplossing

Er zijn verschillende dingen die u kunt doen om de synchronisatieproblemen met de catalogus op te lossen.

### Wacht op toe te passen wijzigingen

Zodra u vormt en verbindt, kan het meer dan 30 minuten voor de te creëren index in ES (Elasticsearch) en onderzoeksresultaten duren om terug te keren. Volgende eenmalige productupdates zullen naar verwachting binnen een paar minuten worden geïndexeerd.

### Productgegevens synchroniseren voor een specifieke SKU

Als uw productgegevens niet correct voor een specifieke SKU worden gesynchroniseerd, doe het volgende:

1. Gebruik de volgende SQL-query en controleer of u de gegevens hebt die u verwacht in de kolom `feed_data` . Noteer ook de tijdstempel van `modified_at` .

   ```sql
   select * from catalog_data_exporter_products where sku = '<your_sku>' and store_view_code = '<your_ store_view_code>';
   ```

1. Als u de juiste gegevens niet ziet, probeert u deze opnieuw te indexeren met de volgende opdracht en voert u de SQL-query opnieuw uit in stap 1 om de gegevens te verifiëren:

   ```bash
   bin/magento indexer:reindex catalog_data_exporter_products
   ```

1. Als u nog niet de correcte gegevens ziet, [ creeer een kaartje van de Steun ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Tijdstempel controleren van laatste export van product

1. Als u de juiste gegevens ziet in `catalog_data_exporter_products` , gebruikt u de volgende SQL-query om de tijdstempel van de laatste export te controleren. Deze moet na het tijdstempel `modified_at` staan:

   ```sql
   select * from flag where flag_code = 'products-feed-version';
   ```

1. Als de tijdstempel ouder is, kunt u wachten op de volgende uitsnijding of deze zelf activeren met de volgende opdracht:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Wacht op `<>` tijd (tijd voor stijgende updates). Als u nog niet uw gegevens ziet, [ creeer een kaartje van de Steun ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Specifieke kenmerkcode synchroniseren

Als de gegevens van uw productkenmerk niet correct zijn gesynchroniseerd voor een specifieke kenmerkcode, doet u het volgende:

1. Gebruik de volgende SQL-query en controleer of u de gegevens hebt die u verwacht in de kolom `feed_data` . Noteer ook de tijdstempel van `modified_at` .

   ```sql
   select * from catalog_data_exporter_product_attributes where json_extract(feed_data, '$.attributeCode') = '<your_attribute_code>' and store_view_code = '<your_ store_view_code>';
   ```

1. Als u de juiste gegevens niet ziet, gebruikt u de volgende opdracht om de SQL-query opnieuw te indexeren en voert u deze vervolgens opnieuw uit in stap 1 om de gegevens te verifiëren.

   ```bash
   bin/magento indexer:reindex catalog_data_exporter_product_attributes
   ```

1. Als u nog niet de correcte gegevens ziet, [ creeer een kaartje van de Steun ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Tijdstempel controleren van laatste export van productkenmerk

Als u de juiste gegevens ziet in `catalog_data_exporter_product_attributes` :

1. Gebruik de volgende SQL-query om de tijdstempel van de laatste export te controleren. Dit moet na het tijdstempel van `modified_at` staan.

   ```sql
   select * from flag where flag_code = 'product-attributes-feed-version';
   ```

1. Als de tijdstempel ouder is, kunt u wachten op de volgende uitsnijding of deze zelf activeren met de volgende opdracht:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Wacht 15-20 minuten (tijd voor incrementele updates). Als u nog niet uw gegevens ziet, gelieve [ een kaartje van de Steun ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) creëren.

### Synchroniseren na wijziging van API-configuratie

(Bekend probleem) Als u de API-configuratie hebt gewijzigd, wat leidt tot een wijziging in de Data Space ID en tot de bevinding dat de wijzigingen in de catalogus niet meer worden gesynchroniseerd, voert u de volgende opdrachten uit:

```bash
bin/magento saas:resync --feed products
bin/magento saas:resync --feed productattributes
```

## Gerelateerde lezing

Zie [ Levende Onderzoek van de Bord ](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/onboarding-overview.html) in onze gebruikersdocumentatie.
