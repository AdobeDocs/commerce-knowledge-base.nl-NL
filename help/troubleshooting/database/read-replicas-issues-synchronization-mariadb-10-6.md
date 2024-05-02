---
title: Lees de Replica-problemen van Adobe Commerce Cloud 2.4.6 met MariaDB 10.6
description: In dit artikel wordt uitgelegd hoe u problemen met Read Replicas op Adobe Commerce Cloud 2.4.6 met MariaDB 10.6 kunt oplossen.
feature: Configuration
role: Developer,Admin
exl-id: b7af1cc3-93ff-40c5-8959-076cedddb56d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Lees de Replica-problemen van Adobe Commerce Cloud 2.4.6 met MariaDB 10.6

Dit artikel biedt oplossingen voor onverwacht gedrag bij gebruik van Read Replicas op Adobe Commerce Cloud 2.4.6 met MariaDB 10.6+.

## Betrokken producten en versies

* MariaDB 10.6+
* Adobe Commerce over wolkeninfrastructuur 2.4.6

## Probleem

Niet-kritische leesbewerkingen geven onjuiste informatie weer.

## Oorzaak

De `slave_parallel_mode` config op het gegevensbestand werd veranderd standaard in *optimistisch* wanneer de waarde *conservatief* en de `synchronous_replication` waarde in Ece-Tools wordt standaard ingesteld op *true* wanneer de waarde *false*.

## Oplossing

1. Controleer of de `slave_parallel_mode` parameter is ingesteld op *conservatief* (u moet [een ondersteuningsticket opvragen](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) als de waarde niet wordt weergegeven als *conservatief*). Voer de volgende opdracht uit om te controleren:

   ```
    MariaDB [main]> show variables like 'slave_parallel_mode';
    +---------------------+--------------+
    | Variable_name       | Value        |
    +---------------------+--------------+
    | slave_parallel_mode | conservative |
    +---------------------+--------------+
    1 row in set (0.001 sec)
   ```

1. Bijwerken `.magento.env.yaml` databaseconfiguraties naar:

   ```yaml
       DATABASE_CONFIGURATION:
        _merge: true
           slave_connection:
               default:
                   synchronous_replication: false
   ```



Voor stappen bij het bijwerken van de gegevensbestandconfiguratie, verwijs naar [DATABASE_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#database_configuration) in het onderwerp Variabelen distribueren in de Commerce on Cloud Infrastructure Guide.


## Gerelateerde lezing

* [Omgevingsvariabelen voor implementatie configureren](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) in de Commerce on Cloud Infrastructure Guide.
* [Aanbevolen procedures voor databaseconfiguratie](/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) in het afspeelboek van de implementatie.
