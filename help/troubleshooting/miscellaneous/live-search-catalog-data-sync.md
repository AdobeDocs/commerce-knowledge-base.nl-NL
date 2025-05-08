---
title: Live zoekcatalogus is niet gesynchroniseerd
description: Dit artikel biedt oplossingen voor het Adobe Commerce-probleem waarbij de catalogusgegevens niet correct zijn gesynchroniseerd wanneer u de extensie Live zoeken gebruikt.
exl-id: cd2e602f-b2c7-4ecf-874f-ec5f99ae1900
feature: Catalog Management, Search
role: Developer
source-git-commit: 5911b436fdcc08e695fb14d35784287945593815
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Live zoekcatalogus is niet gesynchroniseerd

Dit artikel biedt oplossingen voor het Adobe Commerce-probleem waarbij de catalogusgegevens niet correct zijn gesynchroniseerd wanneer u de extensie Live zoeken gebruikt.

## Betrokken producten en versies

* Adobe Commerce 2.4.x met Live Search-extensie geïnstalleerd

## Probleem

De catalogusgegevens zijn niet correct gesynchroniseerd of er is een nieuw product toegevoegd, maar dit wordt niet weergegeven in de zoekresultaten. U kunt ook de volgende fout in `var/log/exception.log` krijgen:

`Magento_LiveSearch: An error occurred in search backend. {"result":{"errors":[{"message":"Exception while fetching data (/productSearch) : No index was found for this request"}]}}`

>[!NOTE]
>
>De tabelnamen `catalog_data_exporter_products` en `catalog_data_exporter_product_attributes` worden nu `cde_products_feed` en `cde_product_attributes_feed` opgeroepen vanaf [!DNL Live Search] versie 4.2.1. Voor handelaren in versies ouder dan 4.2.1 zoekt u de gegevens in de oude tabelnamen `catalog_data_exporter_products` en `catalog_data_exporter_product_attributes` .

<u> Stappen om te reproduceren </u>

1. Vorm en verbind Levende Onderzoek voor uw instantie van Adobe Commerce zoals die in [ wordt beschreven installeer Levende Onderzoek > vormen API sleutels ](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#configure-api-keys) in onze gebruikersdocumentatie.
1. Na 30 minuten, verifieer de uitgevoerde catalogusgegevens zoals die in [ worden beschreven installeer Levende Onderzoek > verifieer de uitvoer ](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#verify-export) in onze gebruikersdocumentatie.
1. Na 30 minuten, test de verbinding zoals die in [ wordt beschreven installeer Levende Onderzoek > test de verbinding ](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#test-connection) in onze gebruikersdocumentatie.

of

1. Voeg een nieuw product toe aan de catalogus.
1. Probeer een zoekquery uit te voeren met de productnaam of andere doorzoekbare kenmerken na 15-20 minuten vanaf het moment dat Magento indexer + cron wordt uitgevoerd om gegevens te synchroniseren naar de back-endservice.

<u> Verwacht resultaat </u>

* Geëxporteerde catalogusgegevens kunnen worden geverifieerd
* Verbinding is gelukt
* Nieuw product wordt weergegeven in zoekresultaten.

<u> Werkelijk resultaat </u>

De geëxporteerde catalogus kan niet worden geverifieerd en/of de verbinding is niet tot stand gebracht omdat de API-sleutel is gewijzigd.

## Oplossing

Er zijn verschillende dingen die u kunt doen om de synchronisatieproblemen met de catalogus op te lossen.

### Wacht op toe te passen wijzigingen

Nadat u de configuratie en verbinding hebt gemaakt, kan het meer dan 30 minuten duren voordat de index in ES (Elasticsearch) is gemaakt en de zoekresultaten zijn geretourneerd. Volgende eenmalige productupdates zullen naar verwachting binnen een paar minuten worden geïndexeerd.

### Productgegevens synchroniseren voor een specifieke SKU

Als uw productgegevens niet correct voor een specifieke SKU worden gesynchroniseerd, doe het volgende:

1. Gebruik de volgende [!DNL SQL] -query en controleer of u de gegevens hebt die u verwacht in de `feed_data` -kolom. Noteer ook de tijdstempel van `modified_at` .

   ```sql
   SELECT * FROM cde_products_feed WHERE json_extract(feed_data, '$.sku') = '<your_sku>' AND json_extract(feed_data, '$.storeViewCode') = '<your_ store_view_code>';
   ```

   Bijvoorbeeld:

   ```sql
   SELECT * FROM cde_products_feed WHERE json_extract(feed_data, '$.sku') = '24-MB04' AND json_extract(feed_data, '$.storeViewCode') = 'default';
   ```

1. Als u de juiste gegevens niet ziet, probeert u deze opnieuw te indexeren met de volgende opdracht en voert u de query [!DNL SQL] opnieuw uit in stap 1 om de gegevens te verifiëren:

   ```bash
   bin/magento indexer:reindex cde_products_feed
   ```

1. Als u nog niet de correcte gegevens ziet, [ creeer een kaartje van de Steun ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Tijdstempel controleren van laatste export van product

1. Als u de juiste gegevens ziet in `cde_products_feed` , gebruikt u de volgende [!DNL SQL] -query om de tijdstempel van de laatste export te controleren. Deze moet na het tijdstempel `modified_at` staan:

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. Als de tijdstempel ouder is, kunt u wachten op de volgende uitsnijding of deze zelf activeren met de volgende opdracht:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Wacht op `<>` tijd (tijd voor stijgende updates). Als u nog niet uw gegevens ziet, [ creeer een kaartje van de Steun ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Specifieke kenmerkcode synchroniseren

Als de gegevens van uw productkenmerk niet correct zijn gesynchroniseerd voor een specifieke kenmerkcode, doet u het volgende:

1. Gebruik de volgende [!DNL SQL] -query en controleer of u de gegevens hebt die u verwacht in de `feed_data` -kolom. Noteer ook de tijdstempel van `modified_at` .

   ```sql
   select * from cde_product_attributes_feed where json_extract(feed_data, '$.attributeCode') = '<your_attribute_code>' and store_view_code = '<your_ store_view_code>';
   ```

1. Als u de juiste gegevens niet ziet, gebruikt u de volgende opdracht om de query opnieuw te indexeren en voert u de query [!DNL SQL] in stap 1 opnieuw uit om de gegevens te verifiëren.

   ```bash
   bin/magento indexer:reindex cde_product_attributes_feed
   ```

1. Als u nog niet de correcte gegevens ziet, [ creeer een kaartje van de Steun ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Tijdstempel controleren van laatste export van productkenmerk

Als u de juiste gegevens ziet in `cde_product_attributes_feed` :

1. Gebruik de volgende [!DNL SQL] query om de tijdstempel van de laatste export te controleren. Dit moet na het tijdstempel van `modified_at` staan.

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. Als de tijdstempel ouder is, kunt u wachten op de volgende uitsnijding of deze zelf activeren met de volgende opdracht:

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. Wacht 15-20 minuten (tijd voor incrementele updates). Als u nog niet uw gegevens ziet, gelieve [ een kaartje van de Steun ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) creëren.

### Synchroniseren na wijziging van API-configuratie

(Bekend probleem) Als u uw API-configuratie hebt gewijzigd, wat resulteert in een wijziging in uw Data Space ID en als u constateert dat de wijzigingen in de catalogus niet meer worden gesynchroniseerd, voert u de volgende opdrachten uit om de feeds opnieuw te synchroniseren:

```
bin/magento saas:resync --feed productattributes --cleanup-feed
bin/magento saas:resync --feed products --cleanup-feed
bin/magento saas:resync --feed scopesCustomerGroup --cleanup-feed
bin/magento saas:resync --feed scopesWebsite --cleanup-feed
bin/magento saas:resync --feed prices --cleanup-feed
bin/magento saas:resync --feed productOverrides --cleanup-feed
bin/magento saas:resync --feed variants --cleanup-feed
bin/magento saas:resync --feed categories --cleanup-feed
bin/magento saas:resync --feed categoryPermissions --cleanup-feed
```

[ leg een steunverzoek ](https://experienceleague.adobe.com/home?support-tab=home#support) voor om herdex van de Levende index van het Onderzoek te verzoeken. Neem in de beschrijving van de uitgave de ID Gegevensruimte/Omgeving op in het deelvenster Beheer onder **[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Commerce Services Connector]** .

>[!IMPORTANT]
>Als u in andere gevallen de optie `--cleanup-feed` gebruikt, kunnen er problemen met gegevensverlies en gegevenssynchronisatie optreden.  Gebruik het slechts wanneer u een nieuw, leeg milieu hebt, nadat het team van Adobe een opschoonverrichting van de gegevensruimte heeft voltooid, of wanneer u het `saas:resync` bevel met [ - droog-looppas ](https://experienceleague.adobe.com/en/docs/commerce/saas-data-export/data-export-cli-commands#--dry-run) optie in werking stelt. Als u in andere gevallen de optie `--cleanup-feed` gebruikt, kunnen er problemen met gegevensverlies en gegevenssynchronisatie optreden.

## Gerelateerde lezing

* [ Levend Onderzoek van de Bord ](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/onboarding-overview.html) in onze gebruikersdocumentatie
* [ Logboeken van het Overzicht en los de gegevensuitvoer en synchronisatie van Adobe Commerce SaaS ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging) in de Gids van de Uitvoer van Gegevens van Adobe Commerce SaaS problemen op
* [ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
