---
title: "Implementatie mislukt: er zijn geen opdrachten gedefinieerd in de naamruimtefout 'cache'"
description: Dit artikel biedt een oplossing voor het probleem wanneer de implementatie mislukt vanwege de volgende fout **Er zijn geen opdrachten gedefinieerd in de cachenaamruimte**.
feature: Deploy
role: Developer
exl-id: ee2bddba-36f7-4aae-87a1-5dbeb80e654e
source-git-commit: 1a8a4e1eada859a6712a43536d7bad26d1ce1244
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Implementatie mislukt: er zijn geen opdrachten gedefinieerd in de naamruimtefout &#39;cache&#39;

>[!WARNING]
>
>Maak eerst een back-up van de database als u dit doet op een live productiesite, voordat u deze stappen uitvoert.

Dit artikel verstrekt een oplossing voor de kwestie wanneer uw plaatsing ontbreekt en één van de fouten in het logboek als dit kijkt:

```
[YEAR-DAYTIME] ERROR: [127] The command "php ./bin/magento cache:flush --ansi --no-interaction" failed.
        There are no commands defined in the "cache" namespace.
...
      W:     There are no commands defined in the "cache" namespace.
```

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur 2.4.x

## Probleem  

<u>Stappen om te reproduceren</u>:

Poging om te implementeren. 

<u>Verwachte resultaten</u>:

De implementatie is voltooid.

<u>Werkelijke resultaten</u>:

U kunt niet correct implementeren. In de logboeken ziet u een plaatsingsfout met een bericht gelijkend op het volgende *Er zijn geen opdrachten in de cachenaamruimte*.

### Oorzaak

De **core_config_data** tabel bevat configuraties voor een winkel-id of website-id die niet meer in de database aanwezig zijn. Dit gebeurt wanneer u een databaseback-up hebt geïmporteerd uit een andere instantie/omgeving en de configuraties voor die bereikinstellingen in de database blijven, hoewel de bijbehorende opslag(en)/website(s) zijn verwijderd.

### Oplossing

Als u maar één website hebt, is de tweede test voor de websites niet van toepassing en hoeft u alleen maar te testen op winkels.

Om dit probleem op te lossen, identificeer de ongeldige rijen die van die configuraties worden verlaten.

1. SSH aan de server en stel dit bevel in werking:

   `bin/magento`

1. Het foutbericht geeft mogelijk aan welke rijen en tabellen in de database blijven van verwijderde sites. Hieronder ziet u bijvoorbeeld een fout die aangeeft dat de gevraagde opslag niet is gevonden:

   ```...
   In StoreRepository.php line 112:
   
   The store that was requested wasn't found. Verify the store and try again.
   ```

1. Voer deze MySql-query uit om te controleren of de winkel niet kan worden gevonden. Dit wordt aangegeven door het foutbericht in stap 2. 

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Voer de volgende MySql-instructie uit om de ongeldige rijen te verwijderen: 

   ```sql
   delete from core_config_data where scope='stores' and scope_id not in (select store_id from store); 
   ```

1. Voer deze opdracht opnieuw uit:

   `bin/magento`

   Als u een fout krijgt zoals hieronder die erop wijst dat de website met id X die werd gevraagd niet werd gevonden u configuraties in het gegevensbestand van website(s) evenals opslag(s) hebt die zijn geschrapt.

   ```
   In WebsiteRepository.php line 110:
   
   The website with id X that was requested wasn't found. Verify the website and try again.
   ```

   Voer deze MySql-query uit en controleer of de website niet is gevonden:

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Voer deze MySql-instructie uit om de ongeldige rijen uit de websiteconfiguratie te verwijderen:

   ```sql
   delete from core_config_data where scope='websites' and scope_id not in (select website_id from store_website);
   ```

Om te bevestigen dat de oplossing werkte, stel `bin/magento` opnieuw gebruiken. U zou niet meer de fouten moeten zien en met succes kunnen opstellen.

## Gerelateerde lezing

* [Adobe Commerce-probleemoplossing voor implementatie](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter.html)
* [Implementatielogbestand controleren als in de gebruikersinterface van Cloud een fout met een &#39;log snipped&#39; is opgetreden](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error.html)
