---
title: Database-dump maken op Adobe Commerce op cloudinfrastructuur
description: In dit artikel worden de mogelijke (en aanbevolen) manieren besproken om een database (DB)-stortplaats op Adobe Commerce te maken op cloudinfrastructuur.
exl-id: 4a2e54ac-8d65-4e51-8337-08f9748dc6c0
feature: Cloud
source-git-commit: 0948b2a94ee4f2a355e7c024a09929f0ad223783
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Database-dump maken op Adobe Commerce op cloudinfrastructuur

In dit artikel worden de mogelijke (en aanbevolen) manieren besproken om een database (DB)-stortplaats op Adobe Commerce te maken op cloudinfrastructuur.

U hoeft slechts één variant (optie) te gebruiken om uw database te dumpen. Deze opties zijn van toepassing op elk type omgeving (integratie, staging, productie) en elk plan (Adobe Commerce on cloud Infrastructure Starter-planarchitectuur en Adobe Commerce on cloud Infrastructure Pro-planarchitectuur).

## Vereiste: SSH voor uw omgeving

Als u uw database op Adobe Commerce wilt dumpen op een cloudinfrastructuur met elke variant die in dit artikel wordt besproken, moet u eerst [SSH voor uw omgeving](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).

>[!WARNING]
>
>Of u Optie 1 of Optie 2 kiest gelieve het bevel tijdens van piekuren tegen een gegevensbestand secundaire knoop in werking te stellen.

## Optie 1: db-dump (**Gereedschap voor kinderen; aanbevolen**)

U kunt uw database dumpen met de [ECE-gereedschappen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) opdracht:

```php
vendor/bin/ece-tools db-dump
```

Dit is de aanbevolen en veiligste optie.

Zie [De database dumpen (ECE-tools)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/database-dump.html) in onze Commerce on Cloud Infrastructure Guide.

## Optie 2: mysqldump

>[!WARNING]
>
>Voer deze opdracht niet uit in de databasecluster. De cluster zal niet onderscheiden of het tegen het gegevensbestand primair of tegen een secundair wordt in werking gesteld. Als de cluster dit bevel tegen primair in werking stelt, zal het gegevensbestand schrijven niet kunnen uitvoeren tot de stortplaats wordt voltooid en prestaties en plaatsstabiliteit zou kunnen beïnvloeden.

U kunt uw OB dumpen gebruikend inheemse MySQL `mysqldump` gebruiken.

Het volledige bevel zou als volgt kunnen kijken:

```sql
mysqldump -h <host> -u <username> -p <password> --single-transaction <db_name> | gzip > /tmp/<dump_name>.sql.gz
```

De databaseback-up die is gemaakt door het uitvoeren van de `mysqldump` opdracht en opgeslagen in `\tmp`, moet u deze locatie verlaten. Het moet geen opslagruimte in beslag nemen `\tmp` (die tot problemen kunnen leiden).

Om uw geloofsbrieven van DB (gastheer, gebruikersbenaming, en wachtwoord) te verkrijgen, zou u kunnen roepen `MAGENTO_CLOUD_RELATIONSHIPS` omgevingsvariabele:

```
echo $MAGENTO_CLOUD_RELATIONSHIPS |base64 --d |json_pp
```

**Verwante documentatie:**

* [mysqldump - Een back-upprogramma voor databases](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) in officiële MySQL-documentatie.
* [Cloudspecifieke variabelen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html) (zie `MAGENTO_CLOUD_RELATIONSHIPS`) in onze Commerce on Cloud Infrastructure Guide.
