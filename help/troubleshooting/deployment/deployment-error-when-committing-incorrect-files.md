---
title: Implementatiefouten bij het uitvoeren van onjuiste bestanden
description: Dit artikel biedt een oplossing voor het probleem wanneer u implementatiefouten krijgt die worden veroorzaakt door onjuiste verbintenissen aan de opslagplaats van bestanden/mappen die niet hadden moeten worden toegevoegd.
feature: Deploy
role: Developer
exl-id: c795f9d5-7171-4846-b99f-c018f1d2bf12
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Implementatiefouten bij het uitvoeren van onjuiste bestanden

Dit artikel biedt een oplossing voor het probleem wanneer u implementatiefouten krijgt die worden veroorzaakt door onjuiste opdrachten in de opslagplaats van bestanden/mappen die niet hadden moeten worden toegevoegd.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur (alle versies)

## Probleem

Er treden implementatiefouten op wanneer u bestanden/mappen opslaat in de opslagplaats. De volgende fout wordt bijvoorbeeld veroorzaakt door een poging om verbinding te maken met de database wanneer deze momenteel niet beschikbaar is tijdens het dialoogvenster [Fase samenstellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#build-phase):

```SQL
SQLSTATE[HY000] [2002] php_network_getaddresses: getaddrinfo for database.i  
          nternal failed: Name or service not known                                    
                                                                                       
        
        In Abstract.php line 124:
                                                                                       
          SQLSTATE[HY000] [2002] php_network_getaddresses: getaddrinfo for database.i  
          nternal failed: Name or service not known                                    
                                                                                       
        
        In Abstract.php line 124:
                                                                                       
          PDO::__construct(): php_network_getaddresses: getaddrinfo for database.inte  
          rnal failed: Name or service not known       
```

## Oorzaak

Bepaalde bestanden/mappen moeten niet worden toegewezen aan de opslagplaats, omdat ze een onderbreking veroorzaken in de [implementatieworkflow](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html).

## Oplossing

Verwijder deze bestanden/mappen uit uw opslagplaats als ze aanwezig zijn:

* `app/etc/env.php`
* `pub/media/catalog`
* `vendor`
