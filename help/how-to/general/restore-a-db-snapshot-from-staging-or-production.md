---
title: Een DB-momentopname herstellen uit Staging of Productie
description: In dit artikel wordt getoond hoe u een DB-momentopname van Staging of Production op Adobe Commerce op cloudinfrastructuur kunt herstellen.
exl-id: 1026a1c9-0ca0-4823-8c07-ec4ff532606a
source-git-commit: b9e72ff8d541ad01788e5198e03abcb46a1bd11f
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# Een DB-momentopname herstellen vanuit [!DNL Staging] of [!DNL Production]

In dit artikel wordt getoond hoe u een database kunt herstellen [!DNL snapshot] van [!DNL Staging] of [!DNL Production] op Adobe Commerce op Cloud Pro Infrastructure.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, [alle ondersteunde versies](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Kies de meest geschikte optie voor uw kwestie:

* [Methode 1: De database overbrengen [!DNL dump] naar uw lokale computer en deze importeren](#meth2).
* [Methode 2: De database importeren [!DNL dump] rechtstreeks vanaf de server](#meth3).

## Methode 1: De database overbrengen [!DNL dump] naar uw lokale computer en deze importeren {#meth2}

De stappen zijn:

1. Gebruiken [!DNL sFTP], navigeer naar de locatie waar de database zich bevindt [!DNL snapshot] is geplaatst, gewoonlijk op de eerste server/de knoop van uw [!DNL cluster] (Bijvoorbeeld: `/mnt/recovery-<recovery_id>`). NOTA: Als uw project op Azure-Gebaseerd is, d.w.z., kijkt uw project URL ongeveer als https://us-a1.magento.cloud/projects/&lt;cluster_id>, wordt de opname geplaatst `/mnt/shared/<cluster ID>/all-databases.sql.gz` of `/mnt/shared/<cluster ID_stg>/all-databases.sql.gz` in plaats daarvan.

   NOTA: Het formaat van de momentopname op Azure projecten zal verschillend zijn en bevat andere gegevensbestanden die niet kunnen worden ingevoerd. Alvorens de momentopname in te voeren, zult u extra stappen moeten nemen om het aangewezen gegevensbestand te halen alvorens de stortplaats in te voeren.

   Voor productie:

   ```sql
   cd /mnt/shared/<cluster ID/
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID>.sql 
   sed -n '/^-- Current Database: `<cluster ID>`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID>.sql gzip <cluster ID>.sql
   zcat <cluster ID>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

   Voor opmaken:

   ```sql
   cd /mnt/shared/<cluster ID/ | cd /mnt/shared/<cluster ID_stg>
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID_stg>.sql
   sed -n '/^-- Current Database: `wyf2o4zlrljjs`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID_stg>.sql 
   gzip <cluster ID_stg>.sql  
   zcat <cluster ID_stg>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

1. De database kopiëren [!DNL dump file] (Bijvoorbeeld: `<cluster ID>.sql.gz` for [!DNL Production] of `<cluster ID_stg>.sql.gz` for [!DNL Staging]) naar uw lokale computer.
1. Zorg ervoor dat u de [!DNL SSH tunnel] op afstand verbinding maken met de database: [[!DNL SSH] en [!DNL sFTP]: [!DNL SSH tunneling]](https://devdocs.magento.com/cloud/env/environments-ssh.html#env-start-tunn) in onze ontwikkelaarsdocumentatie.
1. Maak verbinding met de database.

   ```sql
   mysql -h <db-host> -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] de databank; [!DNL MariaDB] prompt, enter:

   (Voor [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (Voor [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. Voer de volgende opdracht in om de [!DNL snapshot]:

   (Voor [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

   (Voor [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

## Methode 2: De database importeren [!DNL dump] rechtstreeks vanaf de server {#meth3}

De stappen zijn:

1. Ga naar de locatie waar de database zich bevindt [!DNL snapshot] is geplaatst, gewoonlijk op de eerste server/de knoop van uw [!DNL cluster] (Bijvoorbeeld: `/mnt/recovery-<recovery_id>`).
1. Naar [!DNL drop] en maak de clouddatabase opnieuw, maak eerst verbinding met de database:

   ```sql
   mysql -h 127.0.0.1 -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] de databank; [!DNL MariaDB] prompt, enter:

   (Voor [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (Voor [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. Voer de volgende opdracht in om de [!DNL snapshot]:

   (Voor [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Voor [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

## Gerelateerde lezing

In onze documentatie voor ontwikkelaars:

* [Code importeren: de database importeren](https://devdocs.magento.com/cloud/setup/first-time-setup-import-import.html#cloud-import-db)
* [[!DNL Snapshots] en [!DNL backup] management: [!DNL Dump] uw database](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump)
