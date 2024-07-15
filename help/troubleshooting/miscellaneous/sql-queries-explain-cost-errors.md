---
title: '''SQL query''s: UITSPELEN van kostenfouten'''
description: Dit artikel biedt oplossingen voor EXPLAIN-kostenfouten bij het uitvoeren van mislukte SQL-query's. PostgreSQL gebruikt iets genoemd [het bevel EXPLAIN] (https://www.postgresql.org/docs/9.5/static/using-explain.html) om de kosten van SQL vragen te bepalen. Wij bouwden de SQL Report Builder om dit bevel ook te gebruiken, betekenend dat als de kosten te hoog worden geacht - de hoeveelheid middelen die worden vereist om de vraag uit te voeren onze drempels overschrijdt - de vraag niet zal lopen en een EXPLAIN bericht zal tonen.
exl-id: 6f6df66a-665e-46a8-ad4c-842a0270c4eb
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# SQL-query&#39;s: EXPLAIN-kostenfouten

Dit artikel biedt oplossingen voor EXPLAIN-kostenfouten bij het uitvoeren van mislukte SQL-query&#39;s. PostSQL gebruikt iets genoemd [ het bevel EXPLAIN ](https://www.postgresql.org/docs/9.5/static/using-explain.html) om de kosten van SQL vragen te bepalen. Wij bouwden de SQL Report Builder om dit bevel ook te gebruiken, betekenend dat als de kosten te hoog worden geacht - de hoeveelheid middelen die worden vereist om de vraag uit te voeren onze drempels overschrijdt - de vraag niet zal lopen en een EXPLAIN bericht zal tonen.

Er zijn enkele redenen waarom dit zou kunnen gebeuren. Hier zijn de berichten u zou kunnen ontvangen, wat zij betekenen, en hoe te om hen problemen op te lossen.

## Kan query niet uitvoeren. De EXPLAIN-kostenwaarde van \[xxx\] is te hoog om deze query uit te voeren.

Als dit bericht wordt weergegeven, betekent dit dat de query te duur werd geacht om te worden uitgevoerd. Wij hebben twee aanbevelingen voor deze situatie: één moet om het even welke ORDER DOOR clausules van uw vraag elimineren, aangezien zij dure verrichtingen zijn. De tweede moet de uiteinden in ons [ optimaliseringsartikel ](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/optimizing-your-sql-queries.html) volgen om uw vraag te tweken.

## Kan query niet uitvoeren. Deze query retourneert \[xxx\] rijen die onze limiet van 10.000 overschrijden

In dit geval overschrijdt het mogelijke aantal resultaten het ingestelde maximum voor de SQL-Report Builder. U kunt het aantal resultaten op een aantal manieren verminderen:

* Voeg enkele filters toe aan de query.
* Gebruik LIMIT als dat mogelijk is. Sommige tabellen hebben een groot aantal rijen en als u de resultaten beperkt, blijft de rijlimiet mogelijk gehandhaafd.

## Kan de EXPLAIN-reactie niet parseren.

Oeps. Dit bericht betekent dat er waarschijnlijk iets verkeerd is gegaan aan onze kant. Neem contact op met de afdeling Ondersteuning als deze fout zich blijft voordoen.
