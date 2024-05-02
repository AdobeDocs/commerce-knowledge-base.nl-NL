---
title: ElasticSuite-volgindices veroorzaken problemen met Elasticsearch
description: In dit artikel wordt gesproken over het probleem van geheugenproblemen bij Elasticsearch die worden veroorzaakt door het bijhouden van indices die door de insteekmodule ElasticSuite worden geproduceerd.
exl-id: 67bfd06a-c801-4306-8510-a84a6fe5351a
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# ElasticSuite-volgindices veroorzaken problemen met Elasticsearch

>[!NOTE]
>
>ElasticSuite en de bijbehorende toepassingen zijn hulpmiddelen van derden die momenteel niet door Adobe worden ondersteund. Deze inhoud wordt alleen ter informatie gepresenteerd en niet als een indicatie van wat is ingeschakeld voor ondersteuningsdekking.

In dit artikel wordt gesproken over het probleem van geheugenproblemen bij Elasticsearch die worden veroorzaakt door het bijhouden van indices die door de insteekmodule ElasticSuite worden geproduceerd.

## Betrokken producten en versies

ElasticSuite-versies ouder dan 2.8.0 kunnen volgindices niet periodiek opschonen.

ElasticSuite-versies die ouder zijn dan 2.9.8 / 2.10.7 slaan traceerindexen op in dagelijkse indexen, waardoor het aantal open indexen toeneemt.

## Probleem

Als de ElasticSuite-insteekmodule van derden is geïnstalleerd, kunnen er geheugenproblemen optreden bij de Elasticsearch en kan de service Elasticsearch vastlopen als gevolg van ElasticSuite-trackingsindices. Symptomen zijn onder meer:

* Elasticsearch loopt vast zonder geheugenfouten.
* Bij het uitvoeren van een opdracht voor gezondheid `curl -m1 localhost:9200/_cluster/health?pretty` of `curl -m1 elasticsearch.internal:9200/_cluster/health?pretty` (voor startaccounts) er zijn honderden of duizenden `unassigned_shards`
* De Elasticsearch- of siteprestaties worden ernstig aangetast.
* *&quot;Geen levende knopen die in uw cluster worden gevonden&quot;* in Elasticsearch stelt of registreert fouten op.
* *&quot;Toewijzingsupdate negeren naar [&lt;\*>_ tracking_log_event _&lt;\*>]&quot;* in opstellen of logboekfouten.

## Oorzaak

ElasticSuite beschikt over een nieuwe functie waarmee traceerindexen worden gemaakt. In deze volgindices wordt vastgelegd welke zoektermen het meest worden gebruikt, welke termen de meeste omzet genereren en welke termen leiden tot een pagina zonder resultaten, zodat verkopers synoniemen kunnen maken om deze te herstellen. Het lijkt niet om de volgende indexen te schrappen, zodat loopt de Elasticsearch uit middelen en crasht.

## Oplossing

### Voer een upgrade uit op uw ElasticSuite-versie om trackingindexen regelmatig op te schonen

Als u de insteekmodule ElasticSuite hebt bijgewerkt naar een hogere versie dan versie 2.8.0, kunt u een periodieke reiniging van indexen configureren.

Ga naar **Winkels** > **Configuratie** > **Tekstspatiëring** > **Algemene configuratie** > **Bewaarvertraging**

De standaardretentieperiode is 365 dagen. U kunt deze terugbrengen tot 30 of 15 dagen.

### Upgrade uw ElasticSuite-versie om maandelijkse indexen in plaats van dagelijkse indexen te gebruiken

Als u de insteekmodule ElasticSuite hebt bijgewerkt naar versie > 2.9.8 / 2.10.7, worden de trackingindexen maandelijks gebaseerd.

U kunt de retentieperiode nog steeds verkorten:

Ga naar **Winkels** > **Configuratie** > **Tekstspatiëring** > **Algemene configuratie** > **Bewaarvertraging**

De standaardretentieperiode is 12 maanden (er worden 12 indexen gegenereerd). U kunt de dosis verlagen tot 3 of 6 maanden.

### Een kronjob gebruiken om gegevens over volgindexen op te schonen

Maak een uitsnijdtaak om de volgende indexen te verwijderen. Met deze opdracht verwijdert u indexen die in de laatste maand zijn gemaakt:

```
   curl -XDELETE localhost:9200/<name in index> * **\_tracking\_log** * _$(date
    +'%Y%m' -d 'last month')*
```

Als u indexen op een vastgestelde tijd-frequentie wilt schrappen, creeer een hulpbaan door naar de volgende artikelen in onze ontwikkelaarsdocumentatie te verwijzen:

* [Een aangepaste uitsnijdtaak en uitsnijdgroep configureren (zelfstudie)](https://devdocs.magento.com/guides/v2.3/config-guide/cron/custom-cron-tut.html)
* [Uitsnijdtaken instellen](https://devdocs.magento.com/guides/v2.3/cloud/configure/setup-cron-jobs.html)
