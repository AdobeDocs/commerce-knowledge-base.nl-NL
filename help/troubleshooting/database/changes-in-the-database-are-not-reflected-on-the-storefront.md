---
title: Wijzigingen in de database worden niet weerspiegeld in de winkel
description: Dit artikel biedt oplossingen om vertragingen of onderbrekingen in de updates van entiteiten te voorkomen. Dit omvat hoe te om veranderingslogboeklijsten te vermijden van het worden overmaats en hoe te opstelling MySQL lijsttrekkers.
exl-id: ac52c808-299f-4d08-902f-f87db1fa7ca6
feature: Catalog Management, Categories, Services, Storefront
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# Wijzigingen in de database worden niet weerspiegeld in de winkel

Dit artikel biedt oplossingen om vertragingen of onderbrekingen in de updates van entiteiten te voorkomen. Dit omvat hoe te om veranderingslogboeklijsten te vermijden van het worden overmaats en hoe te opstelling MySQL lijsttrekkers.

Betrokken producten en versies:

* Adobe Commerce op cloud-infrastructuur 2.2.x, 2.3.x
* Adobe Commerce op locatie 2.2.x, 2.3.x

## Probleem

Wijzigingen die u aanbrengt in de database, worden niet doorgevoerd in de winkel of er is een aanzienlijke vertraging bij de toepassing van entiteitsupdates. Tot de entiteiten die kunnen worden beïnvloed behoren producten, categorieën, prijzen, voorraden, catalogusregels, verkoopregels en doelregels.

## Oorzaak

Als uw indexen [geconfigureerd voor bijwerken volgens schema](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html#configure-indexers), kan de kwestie door één of meerdere lijsten met veranderingslogboeken worden veroorzaakt die te groot zijn of de trekkers MySQL die niet opstelling zijn.

### Te grote logtabellen voor wijzigingen

De lijsten van het veranderingslogboek groeien dat als `indexer_update_all_views` de snijtaak is niet meerdere keren voltooid.

Logtabellen wijzigen zijn de databasetabellen waarin de wijzigingen in entiteiten worden bijgehouden. Een verslag wordt opgeslagen in een lijst van het veranderingslogboek zolang de verandering niet wordt toegepast, die door wordt uitgevoerd `indexer_update_all_views` snijtaak. Een Adobe Commerce-database bevat meerdere veranderingslogtabellen. Deze krijgen een naam volgens het volgende patroon: INDEXER\_TABLE\_NAME + ‘\_cl’, bijvoorbeeld `catalog_category_product_cl`, `catalog_product_category_cl`. Meer informatie over hoe wijzigingen worden bijgehouden in de database vindt u in het dialoogvenster [Overzicht van indexering > Weergave](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#m2devgde-mview) artikel in onze ontwikkelaarsdocumentatie.

### MySQL database triggers not set

U zou vermoeden dat database-triggers niet worden ingesteld, als na het toevoegen of wijzigen van een entiteit (product, categorie, doelregel, enzovoort) geen records worden toegevoegd aan de overeenkomstige tabel in het wijzigingslogboek.

## Oplossing

>[!WARNING]
>
>We raden u ten zeerste aan een back-up van een database te maken voordat u wijzigingen aanbrengt en deze te vermijden tijdens perioden met veel laadtijd.

### Vermijd te grote wijzigingen in logtabellen

Zorg ervoor dat de `indexer_update_all_views` de snijtaak is altijd voltooid.

U kunt de volgende SQL-query gebruiken om alle mislukte instanties van de opdracht `indexer_update_all_views` snijtaak:

```sql
select * from cron_schedule where job_code = "indexer_update_all_views" and status
  <> "success" and status <> "pending";
```

Of u kunt de status in de logboeken controleren door te zoeken naar de `indexer_update_all_views` vermeldingen:

* `<install_directory>/var/log/cron.log` - voor versies 2.3.1+ en 2.2.8+
* `<install_directory>/var/log/system.log` - voor eerdere versies

### MySQL-tabeltriggers opnieuw instellen

Als u de ontbrekende MySQL-tabeltriggers wilt instellen, moet u de indexeermodus opnieuw instellen:

1. Schakel over naar &#39;Bij opslaan&#39;.
1. Schakel terug naar &#39;Op schema&#39;.

Gebruik de volgende opdracht om deze bewerking uit te voeren.

>[!WARNING]
>
>Voordat u van indexeermodus overschakelt, raden we u aan uw website in te zetten [onderhoud](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode) en [uitsnijdtaken uitschakelen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs) om databasestlokken te voorkomen.

```bash
php bin/magento indexer:set-mode {realtime|schedule} [indexerName]
```

>[!INFO]
>
>De indexeerderverwante gegevensbestandtrekkers worden toegevoegd wanneer de indexeerwijze aan programma wordt geplaatst en wordt verwijderd wanneer de indexeerwijze aan realtime wordt geplaatst. Als de triggers ontbreken in uw database terwijl de indexen zijn ingesteld op programmeren, wijzigt u de indexen in realtime en wijzigt u ze weer in schema. Hierdoor worden de triggers opnieuw ingesteld.

## Gerelateerde lezing

<ul><li title="MySQL-tabellen zijn te groot"><a href="/help/troubleshooting/database/mysql-tables-are-too-large.md">MySQL-tabellen zijn te groot</a> in onze kennisbasis voor ondersteuning.</li>
<li title="MySQL-tabellen zijn te groot"><a href="https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#m2devgde-mview">Overzicht van Indexer &gt; Weergave</a> in onze ontwikkelaarsdocumentatie.</li></ul>
