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

Er treden implementatiefouten op wanneer u bestanden/mappen opslaat in de opslagplaats. Bijvoorbeeld, wordt de volgende fout veroorzaakt toe te schrijven aan een poging om met DB te verbinden wanneer het niet momenteel beschikbaar tijdens [&#x200B; is bouwt Fase &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?lang=nl-NL#build-phase):

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

Bepaalde dossiers/omslagen zouden niet aan de bewaarplaats moeten worden geëngageerd, aangezien zij een onderbreking in het [&#x200B; plaatsingswerkschema &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?lang=nl-NL) veroorzaken.

## Oplossing

Verwijder deze bestanden/mappen uit uw opslagplaats als ze aanwezig zijn:

* `app/etc/env.php`
* `pub/media/catalog`
* `vendor`
