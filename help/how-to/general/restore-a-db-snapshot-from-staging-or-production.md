---
title: Een DB-momentopname herstellen uit Staging of Productie
description: In dit artikel wordt getoond hoe u een DB-momentopname van Staging of Production op Adobe Commerce op cloudinfrastructuur kunt herstellen.
exl-id: 1026a1c9-0ca0-4823-8c07-ec4ff532606a
source-git-commit: b99d78845128ca3d995cbbb5df0799449ca954e3
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Een DB-momentopname herstellen vanuit [!DNL Staging] of [!DNL Production]

In dit artikel wordt weergegeven hoe u een database [!DNL snapshot] vanaf [!DNL Staging] of [!DNL Production] op Adobe Commerce kunt herstellen in de Cloud Pro-infrastructuur.

## Betrokken producten en versies

* Adobe Commerce op wolkeninfrastructuur, [ alle gesteunde versies ](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Kies de meest geschikte optie voor uw kwestie:

* [ Methode 1: Breng het gegevensbestand  [!DNL dump]  over aan uw lokale machine en voer het ](#meth2) in.
* [ Methode 2: Importeer het gegevensbestand  [!DNL dump]  direct van de server ](#meth3).

## Methode 1: Breng de database [!DNL dump] over naar de lokale computer en importeer deze. {#meth2}

De stappen zijn:

1. Navigeer met [!DNL SFTP] naar de locatie waar de database [!DNL snapshot] is geplaatst, meestal op de eerste server/het eerste knooppunt van de [!DNL cluster] (bijvoorbeeld: `/mnt/recovery-<recovery_id>`). OPMERKING: als uw project Azure-gebaseerd is, d.w.z. uw project-URL er ongeveer zo uitziet als https://us-a1.magento.cloud/projects/&lt;cluster_id>, wordt de momentopname in plaats daarvan in `/mnt/shared/<cluster ID>/all-databases.sql.gz` of `/mnt/shared/<cluster ID_stg>/all-databases.sql.gz` geplaatst.

   NOTA: Het formaat van de momentopname op Azure projecten zal verschillend zijn en bevat andere gegevensbestanden die niet kunnen worden ingevoerd. Voordat u de opname importeert, gaat u     moeten extra stappen nemen om het aangewezen gegevensbestand te halen alvorens de stortplaats in te voeren.

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

1. Kopieer de database [!DNL dump file] (bijvoorbeeld `<cluster ID>.sql.gz` for [!DNL Production] of `<cluster ID_stg>.sql.gz` for [!DNL Staging] ) naar uw lokale computer.
1. Zorg ervoor u opstelling [!DNL SSH tunnel] om met het gegevensbestand ver hebt te verbinden: [[!DNL SSH]  en  [!DNL sFTP]: [!DNL SSH tunneling] ](https://devdocs.magento.com/cloud/env/environments-ssh.html#env-start-tunn) in onze ontwikkelaarsdocumentatie.
1. Maak verbinding met de database.

   ```sql
   mysql -h <db-host> -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] de database; voer bij de [!DNL MariaDB] -prompt het volgende in:

   (Voor [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (Voor [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. Voer de volgende opdracht in om de [!DNL snapshot] te importeren:

   (Voor [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

   (Voor [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

## Methode 2: Importeer de database [!DNL dump] rechtstreeks vanaf de server {#meth3}

De stappen zijn:

1. Navigeer naar de locatie waar de database [!DNL snapshot] is geplaatst, meestal op de eerste server/node van de [!DNL cluster] (bijvoorbeeld: `/mnt/recovery-<recovery_id>` ).
1. Maak eerst verbinding met de database als u de clouddatabase wilt [!DNL drop] en opnieuw wilt maken:

   ```sql
   mysql -h 127.0.0.1 -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] de database; voer bij de [!DNL MariaDB] -prompt het volgende in:

   (Voor [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (Voor [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. Voer de volgende opdracht in om de [!DNL snapshot] te importeren:

   (Voor het importeren van de back-up van de database vanuit [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Voor het importeren van de back-up van de database vanuit [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Voor het importeren van een databaseback-up vanuit een andere omgeving)

   ```sql
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (Voor het importeren van een databaseback-up vanuit een andere omgeving)

   ```sql
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

## Gerelateerde lezing

In onze documentatie voor ontwikkelaars:

* [ de code van de Invoer: Invoer het gegevensbestand ](https://devdocs.magento.com/cloud/setup/first-time-setup-import-import.html#cloud-import-db)
* [[!DNL Snapshots]  en  [!DNL backup]  beheer: [!DNL Dump]  uw gegevensbestand ](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump)
