---
title: 503-fout op winkelvoorcataloguspagina's met "schending van integriteitsbeperking" in logboeken
description: Dit artikel bevat een patch voor het bekende Adobe Commerce-probleem met cloudinfrastructuur 2.2.0 dat betrekking heeft op het ontoegankelijk maken van voorcataloguspagina's van winkels.
exl-id: ad363744-756a-48b9-ae11-58642e0ca6a4
feature: Catalog Management, Logs
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# 503-fout op winkelvoorcataloguspagina&#39;s met &quot;schending van integriteitsbeperking&quot; in logboeken

>[!NOTE]
>
>Dit artikel biedt een patch als tijdelijke oplossing, maar het probleem is in Adobe Commerce permanent opgelost in de release van versie 2.3.3 van de cloudinfrastructuur en het wordt aanbevolen een upgrade uit te voeren naar versie 2.3.3. Volg de stappen in [ versie van Adobe Commerce van de Verbetering ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) in onze ontwikkelaarsdocumentatie.

Dit artikel biedt een patch voor de bekende Adobe Commerce in de cloud-infrastructuur 2.2.0-kwestie met betrekking tot de ontoegankelijke opslag van voorcataloguspagina&#39;s. Het foutbericht ziet er ongeveer als volgt uit: *schending integriteitsbeperking: 1062 Dubbele vermelding &#39;%entry%&#39; voor sleutel &#39;PRIMARY&#39;, query was: INSERT INTO \&quot;search\_tmp\_%number%*.

## Probleem

Voorste cataloguspagina&#39;s opslaan wordt onverwacht toegankelijk. Het foutenlogboek heeft een foutenbeschrijving gelijkend op het volgende: *schending van de de beperkingsbeperking van de Integriteit: 1062 Dubbele ingang &quot;%entry%&quot;voor sleutel &quot;PRIMARY&quot;, de vraag was: TUSSENVOEGSEL IN \&quot;search\_tmp\_%number%*.

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
* Adobe Commerce op cloudinfrastructuur 2.2.4 (`MDVA-13203_EE_2.2.4_V1_COMPOSER.patch`)

De `MDVA-9590_EE_2.2.0_COMPOSER_v2` -patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce op cloudinfrastructuur 2.0.X, 2.1.X, 2.2.X en 2.3.0 - 2.3.3
* Adobe Commerce op locatie 2.0.X, 2.1.X, 2.2.X en 2.3.0 - 2.3.3

De `MDVA-13203_EE_2.2.4_V1_COMPOSER` -patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce op cloudinfrastructuur 2.0.X, 2.1.X, 2.2.X en 2.3.0 - 2.3.3
* Adobe Commerce op locatie 2.0.X, 2.1.X, 2.2.X en 2.3.0 - 2.3.3

## Hoe de pleister aanbrengen

Voor instructies, zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze steunkennisbasis wordt verstrekt.

## Nuttige koppelingen

* [ plaats van de dossiers van het Logboek voor Adobe Commerce op het planarchitectuur van de Aanzet van de wolkeninfrastructuur ](/help/how-to/general/log-locations-directories-for-starter-plan.md) in onze basis van de steunkennis.
* [ plaats van de dossiers van het Logboek voor Adobe Commerce op de architectuur van het Pro plan van de wolkeninfrastructuur ](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) in onze basis van de steunkennis.
* [ plaats van de dossiers van het Logboek voor Adobe Commerce ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) in onze ontwikkelaarsdocumentatie.

## Bijgevoegde bestanden
