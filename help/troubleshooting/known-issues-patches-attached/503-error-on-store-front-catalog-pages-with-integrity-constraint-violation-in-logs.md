---
title: 503-fout op winkelvoorcataloguspagina's met "schending van integriteitsbeperking" in logboeken
description: Dit artikel bevat een patch voor het bekende Adobe Commerce-probleem met cloudinfrastructuur 2.2.0 dat betrekking heeft op het ontoegankelijk maken van voorcataloguspagina's van winkels.
exl-id: ad363744-756a-48b9-ae11-58642e0ca6a4
feature: Catalog Management, Logs
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# 503-fout op winkelvoorcataloguspagina&#39;s met &quot;schending van integriteitsbeperking&quot; in logboeken

>[!NOTE]
>
>Dit artikel biedt een patch als tijdelijke oplossing, maar het probleem is in Adobe Commerce permanent opgelost in de release van versie 2.3.3 van de cloudinfrastructuur en het wordt aanbevolen een upgrade uit te voeren naar versie 2.3.3. Voer de stappen uit in [Adobe Commerce-versie upgraden](https://devdocs.magento.com/cloud/project/project-upgrade.html) in onze ontwikkelaarsdocumentatie.

Dit artikel bevat een patch voor het bekende Adobe Commerce-probleem met cloudinfrastructuur 2.2.0 dat betrekking heeft op het ontoegankelijk maken van voorcataloguspagina&#39;s van winkels, waarbij het foutbericht lijkt op het volgende in log: *Schending van integriteitsbeperking: 1062 Dubbele vermelding &#39;%entry%&#39; voor sleutel &#39;PRIMARY&#39;, query was: INSERT INTO \&#39;search\_tmp\_%number%*.

## Probleem

Voorste cataloguspagina&#39;s opslaan wordt onverwacht toegankelijk. Het foutenlogboek heeft een foutenbeschrijving gelijkend op het volgende: *Schending van integriteitsbeperking: 1062 Dubbele vermelding &#39;%entry%&#39; voor sleutel &#39;PRIMARY&#39;, query was: INSERT INTO \&#39;search\_tmp\_%number%*.

Het probleem houdt verband met zoeken en wordt veroorzaakt door het bestaan van de verouderde index samen met de nieuwe index na herdex.

## Oplossing

Om het probleem te bevestigen, moet u verouderde indexen uit Elasticsearch verwijderen en het flard toepassen om hen te verhinderen te verschijnen.

Als u alle indexen wilt weergeven, gebruikt u de volgende opdracht:

<pre>curl -X GET %elasticsearch_domain%:%elasticsearch_port%/_cat/indices</pre>

Om de verouderde indexen te verwijderen, vind hen in het gegevensbestand en gebruik dan het volgende bevel:

```bash
curl -X DELETE %elasticsearch_domain%:%elasticsearch_port%/%product_id%_v%outdated_version%
```

Voorbeeld:

```bash
curl -X DELETE 127.0.0.1:9200/magento2_product_8_v332
```

## Reparatie

De patches zijn aan dit artikel gekoppeld. Als u een patch wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de gewenste bestandsnaam of op een van de volgende koppelingen:

[MDVA-9590\_EE\_2.2.0\_COMPOSER\_v2.patch downloaden](assets/MDVA-9590_EE_2.2.0_COMPOSER_v2.patch.zip)

[Download MDVA-13203\_EE\_2.2.4\_V1\_COMPOSER.patch](assets/MDVA-13203_EE_2.2.4_V1_COMPOSER.patch.zip)

## Compatibele Adobe Commerce-versies

De patches zijn gemaakt voor de volgende versies en versies:

* Adobe Commerce on cloud Infrastructure 2.2.0 (`MDVA-9590_EE_2.2.0_COMPOSER_v2.patch`)
* Adobe Commerce over wolkeninfrastructuur 2.2.4 (`MDVA-13203_EE_2.2.4_V1_COMPOSER.patch`)

De `MDVA-9590_EE_2.2.0_COMPOSER_v2` patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce op cloudinfrastructuur 2.0.X, 2.1.X, 2.2.X en 2.3.0 - 2.3.3
* Adobe Commerce op locatie 2.0.X, 2.1.X, 2.2.X en 2.3.0 - 2.3.3

De `MDVA-13203_EE_2.2.4_V1_COMPOSER` patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce op cloudinfrastructuur 2.0.X, 2.1.X, 2.2.X en 2.3.0 - 2.3.3
* Adobe Commerce op locatie 2.0.X, 2.1.X, 2.2.X en 2.3.0 - 2.3.3

## Hoe de pleister aanbrengen

Zie voor instructies [Hoe een door Adobe geleverde componentpleister aanbrengen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze kennisbasis voor ondersteuning.

## Nuttige koppelingen

* [Locatie van logbestanden voor Adobe Commerce op Starter-planarchitectuur voor cloudinfrastructuur](/help/how-to/general/log-locations-directories-for-starter-plan.md) in onze kennisbasis voor ondersteuning.
* [Locatie van logbestanden voor Adobe Commerce op de Pro-planarchitectuur van de cloud-infrastructuur](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) in onze kennisbasis voor ondersteuning.
* [Locatie van logbestanden voor Adobe Commerce](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html) in onze ontwikkelaarsdocumentatie.

## Bijgevoegde bestanden
