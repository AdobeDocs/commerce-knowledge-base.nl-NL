---
title: Wijzigingen in de database worden niet weerspiegeld in de winkel
description: Dit artikel biedt oplossingen om vertragingen of onderbrekingen in de updates van entiteiten te voorkomen. Dit omvat hoe te om veranderingslogboeklijsten te vermijden van het krijgen van overmaatse en hoe te opstelling  [!DNL MySQL]  lijsttrekkers.
exl-id: ac52c808-299f-4d08-902f-f87db1fa7ca6
feature: Catalog Management, Categories, Services, Storefront
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# Wijzigingen in de database worden niet weerspiegeld in de winkel

Dit artikel biedt oplossingen om vertragingen of onderbrekingen in de updates van entiteiten te voorkomen. Dit omvat hoe te vermijden veranderingslogboeklijsten van het worden overmaats en hoe te opstelling [!DNL MySQL] lijsttrekkers.

Betrokken producten en versies:

* Adobe Commerce op cloud-infrastructuur 2.2.x, 2.3.x
* Adobe Commerce op locatie 2.2.x, 2.3.x

## Probleem

Wijzigingen die u aanbrengt in de database, worden niet doorgevoerd in de winkel of er is een aanzienlijke vertraging bij de toepassing van entiteitsupdates. Tot de entiteiten die kunnen worden beïnvloed behoren producten, categorieën, prijzen, voorraden, catalogusregels, verkoopregels en doelregels.

## Oorzaak

Als uw indexeerders [ worden gevormd om door programma ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers) bij te werken, zou de kwestie door één of meerdere lijsten met veranderingslogboeken kunnen worden veroorzaakt die te groot zijn of trekkers MySQL die niet opstelling zijn.

### Te grote logtabellen voor wijzigingen

De logtabellen voor wijzigingen worden zo groot als de `indexer_update_all_views` -uitsnijdtaak niet meerdere keren is voltooid.

Logtabellen wijzigen zijn de databasetabellen waarin de wijzigingen in entiteiten worden bijgehouden. Een record wordt opgeslagen in een tabel met het wijzigingslogboek, zolang de wijziging niet wordt toegepast. Deze wijziging wordt uitgevoerd door de `indexer_update_all_views` -snijtaak. Een Adobe Commerce-database bevat meerdere veranderingslogtabellen. Deze krijgen een naam volgens het volgende patroon: INDEXER\_TABLE\_NAME + &#39;\_cl&#39;, bijvoorbeeld `catalog_category_product_cl`, `catalog_product_category_cl` . U kunt meer details op vinden hoe de veranderingen in gegevensbestand in het [ Indexeren overzicht > artikel van de Mview ](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) in onze ontwikkelaarsdocumentatie worden gevolgd.

### [!DNL MySQL] database-triggers niet ingesteld

U zou vermoeden dat database-triggers niet worden ingesteld, als na het toevoegen of wijzigen van een entiteit (product, categorie, doelregel, enzovoort) geen records worden toegevoegd aan de overeenkomstige tabel in het wijzigingslogboek.

## Oplossing

>[!WARNING]
>
>We raden u ten zeerste aan een back-up van een database te maken voordat u wijzigingen aanbrengt en deze te vermijden tijdens perioden met veel laadtijd.

### Vermijd te grote wijzigingen in logtabellen

Zorg ervoor dat de `indexer_update_all_views` -snijtaak altijd met succes is voltooid.

U kunt de volgende SQL-query gebruiken om alle mislukte instanties van de `indexer_update_all_views` cron-taak op te halen:

```sql
select * from cron_schedule where job_code = "indexer_update_all_views" and status
  <> "success" and status <> "pending";
```

U kunt ook de status van het bestand in de logboeken controleren door naar de `indexer_update_all_views` -items te zoeken:

* `<install_directory>/var/log/cron.log` - voor versies 2.3.1+ en 2.2.8+
* `<install_directory>/var/log/system.log` - voor eerdere versies

### [!DNL MySQL] tabeltriggers opnieuw instellen

Als u de ontbrekende [!DNL MySQL] tabeltriggers wilt instellen, moet u de indexeermodus opnieuw instellen:

1. Schakel over naar &#39;Bij opslaan&#39;.
1. Schakel terug naar &#39;Op schema&#39;.

Gebruik de volgende opdracht om deze bewerking uit te voeren.

>[!WARNING]
>
>Alvorens de wijzen van de omschakelingsindexeerder, adviseren wij het zetten van uw website in [ onderhoud ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode) wijze en [ bouwbanen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs) onbruikbaar maken om gegevensbestandsloten te vermijden.

```bash
php bin/magento indexer:set-mode {realtime|schedule} [indexerName]
```

>[!INFO]
>
>De indexeerderverwante gegevensbestandtrekkers worden toegevoegd wanneer de indexeerwijze aan programma wordt geplaatst en wordt verwijderd wanneer de indexeerwijze aan realtime wordt geplaatst. Als de triggers ontbreken in uw database terwijl de indexen zijn ingesteld op programmeren, wijzigt u de indexen in realtime en wijzigt u ze weer in schema. Hierdoor worden de triggers opnieuw ingesteld.

## Gerelateerde lezing

* [[!DNL MySQL]  de lijsten zijn te groot ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-tables-are-too-large) in onze basis van de steunkennis
* [ Indexeren: [!DNL Mview] ](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) in onze ontwikkelaarsdocumentatie
* [ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
