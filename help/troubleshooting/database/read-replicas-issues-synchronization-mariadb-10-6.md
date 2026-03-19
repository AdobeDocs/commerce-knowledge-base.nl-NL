---
title: Lees de problemen met replica's over Adobe Commerce Cloud 2.4.6 met MariaDB 10.6
description: In dit artikel wordt uitgelegd hoe u problemen met Read Replicas in Adobe Commerce Cloud 2.4.6 met MariaDB 10.6 kunt oplossen.
feature: Configuration
role: Developer,Admin
exl-id: b7af1cc3-93ff-40c5-8959-076cedddb56d
source-git-commit: 724a30310c3841f8280628436925f9a3e5933b14
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Lees de problemen met replica&#39;s over Adobe Commerce Cloud 2.4.6 met MariaDB 10.6

Dit artikel biedt oplossingen voor onverwacht gedrag bij het gebruik van Read Replicas op Adobe Commerce Cloud 2.4.6 met MariaDB 10.6+.

## Betrokken producten en versies

* MariaDB 10.6+
* Adobe Commerce over wolkeninfrastructuur 2.4.6

## Probleem

Niet-kritische leesbewerkingen geven onjuiste informatie weer.

## Oorzaak

`slave_parallel_mode` config op het gegevensbestand werd veranderd door gebrek in *optimistics* wanneer de waarde *conservatief* zou moeten zijn, en de `synchronous_replication` waarde in ce-Tools aan *waar* in gebreke blijft wanneer de waarde *vals* zou moeten zijn.

## Oplossing

1. Controle dat de `slave_parallel_mode` parameter aan *conservatief* wordt geplaatst (u zult een steunkaartje [ moeten opheffen als de waarde niet als ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) conservatief *toont).* Voer de volgende opdracht uit om te controleren:

   ```
    MariaDB [main]> show variables like 'slave_parallel_mode';
    +---------------------+--------------+
    | Variable_name       | Value        |
    +---------------------+--------------+
    | slave_parallel_mode | conservative |
    +---------------------+--------------+
    1 row in set (0.001 sec)
   ```

1. Werk `.magento.env.yaml` databaseconfiguraties bij naar:

   ```yaml
       DATABASE_CONFIGURATION:
        _merge: true
           slave_connection:
               default:
                   synchronous_replication: false
   ```



Voor stappen bij het bijwerken van de gegevensbestandconfiguratie, verwijs naar [ DATABASE_CONFIGURATION ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#database_configuration) in het Deploy variabelen onderwerp in Commerce op de Gids van de Infrastructuur van de Wolk.


## Gerelateerde lezing

* [ vorm milieuvariabelen voor plaatsing ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) in Commerce op de Gids van de Infrastructuur van de Wolk.
* [ Beste praktijken voor gegevensbestandconfiguratie ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) in het Playbook van de Implementatie.
