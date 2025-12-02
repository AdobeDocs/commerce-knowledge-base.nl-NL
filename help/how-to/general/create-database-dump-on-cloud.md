---
title: Database-dump maken op Adobe Commerce op cloudinfrastructuur
description: In dit artikel worden de mogelijke (en aanbevolen) manieren besproken om een database (DB)-stortplaats op Adobe Commerce te maken op cloudinfrastructuur.
exl-id: 4a2e54ac-8d65-4e51-8337-08f9748dc6c0
feature: Cloud
source-git-commit: 96b145a1f76c296907da96fd97c7a8f7778463f8
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Database-dump maken op Adobe Commerce op cloudinfrastructuur

In dit artikel worden de mogelijke (en aanbevolen) manieren besproken om een database (DB)-stortplaats op Adobe Commerce te maken op cloudinfrastructuur.

U hoeft slechts één variant (optie) te gebruiken om uw database te dumpen. Deze opties zijn van toepassing op elk type omgeving (integratie, staging, productie) en elk plan (Adobe Commerce on cloud Infrastructure Starter-planarchitectuur en Adobe Commerce on cloud Infrastructure Pro-planarchitectuur).

## Vereiste: SSH voor uw omgeving

Om uw OB op Adobe Commerce op wolkeninfrastructuur met om het even welke die variant te dumpen in dit artikel wordt besproken, moet u eerst [ SSH aan uw milieu ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).

>[!WARNING]
>
>Of u Optie 1 of Optie 2 kiest gelieve het bevel tijdens van piekuren tegen een gegevensbestand secundaire knoop in werking te stellen.

## Optie 1: db-stortplaats (**knoop-hulpmiddelen; geadviseerd**)

U kunt uw OB dumpen gebruikend het [ ECE-Hulpmiddelen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) bevel:

```php
vendor/bin/ece-tools db-dump
```

Dit is de aanbevolen en veiligste optie.

Zie [ Dump uw gegevensbestand (ECE-Hulpmiddelen) ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/database-dump.html) in onze Commerce op de Gids van de Infrastructuur van de Wolk.

## Optie 2: mariadb-dump (of mysqldump voor oudere versies)

+++<b> voor nieuwere versies MariaDB (11.x en later) </b>

Vanaf MariaDB 11.0.1 is de symlink `mysqldump` afgekeurd. U wordt aangeraden in plaats daarvan `mariadb-dump` te gebruiken.

Voor meer informatie, verwijs naar [ mariadb-stortplaats cliëntnut ](https://mariadb.com/docs/server/clients-and-utilities/backup-restore-and-import-clients/mariadb-dump).

+++

+++<b> voor oudere versies MariaDB </b> 

Als u zich op een oudere versie van MariaDB bevindt waarvoor `mariadb-dump` niet beschikbaar is, kunt u de DB dumpen met de native opdracht MySQL `mysqldump` .

>[!WARNING]
>
>Voer deze opdracht niet uit in de databasecluster. De cluster zal niet onderscheiden of het tegen het gegevensbestand primair of tegen een secundair wordt in werking gesteld. Als de cluster dit bevel tegen primair in werking stelt, zal het gegevensbestand schrijven niet kunnen uitvoeren tot de stortplaats wordt voltooid en prestaties en plaatsstabiliteit zou kunnen beïnvloeden.

Het volledige bevel zou als volgt kunnen kijken:

```sql
mysqldump -h <host> -u <username> -p <password> --single-transaction <db_name> | gzip > /tmp/<dump_name>.sql.gz
```

De databaseback-up die is gemaakt met de opdracht `mysqldump` en wordt opgeslagen in `\tmp` , moet van deze locatie worden verplaatst. Het zou geen opslagruimte in `\tmp` moeten opnemen (wat in problemen zou kunnen resulteren).

+++

Om uw geloofsbrieven van DB (gastheer, gebruikersbenaming, en wachtwoord) te verkrijgen, zou u de `MAGENTO_CLOUD_RELATIONSHIPS` milieuvariabele kunnen roepen:

```
echo $MAGENTO_CLOUD_RELATIONSHIPS |base64 --d |json_pp
```

**Verwante documentatie:**

* [ mysqldump - een Reservekopieprogramma van het Gegevensbestand ](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) in officiële documentatie MySQL.
* [ wolkenspecifieke variabelen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html) (zie `MAGENTO_CLOUD_RELATIONSHIPS`) in onze Commerce op de Gids van de Infrastructuur van de Wolk.
