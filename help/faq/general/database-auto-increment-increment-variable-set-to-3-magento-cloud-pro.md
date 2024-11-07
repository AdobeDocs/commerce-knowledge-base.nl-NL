---
title: Database auto_increment increment variabele ingesteld op "3" Adobe Commerce op onze cloud pro architectuur
description: Dit is het verwachte gedrag voor Adobe Commerce op cloudinfrastructuur Pro-architectuuroplossingen vanwege de architectuur met drie knooppunten en kan niet worden gewijzigd.
exl-id: ea478cbc-2dc2-41c9-8ea7-7e2f308e5948
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Database auto_increment increment variabele ingesteld op &quot;3&quot; Adobe Commerce op onze cloud pro architectuur

Dit is het verwachte gedrag voor Adobe Commerce op cloudinfrastructuur Pro-architectuuroplossingen vanwege de architectuur met drie knooppunten en kan niet worden gewijzigd.

De Galera-databasecluster wordt gebruikt. Dit is een databasecluster met één MariaDB MySQL-database per knooppunt met een instelling voor automatisch verhogen van drie voor unieke id&#39;s in elke database.

<u> waarom wordt increment identiteitskaart die op Pro clusters wordt gebruikt niet altijd gescheiden/verhoogd door 3?</u>

De verhogings-id die in clusters wordt gebruikt, wordt niet altijd met 3 gescheiden/verhoogd vanwege de manier waarop Galera werkt.

Elk van de drie servers beheert zijn eigen ruimte van identiteitskaart, en de toename die afhangt van welke MySQL belangrijkste gegevensbestandserver (afhankelijk van de relatieve lading) is - vandaar de variërende hiaten.
Als u SSH aan elke knoop verbindt en met de lokale instantie MySQL verbindt die op die knoop gebruikend haven 3307 loopt (in plaats van proxied aan &quot;hoofd&quot;op de standaardhaven 3306), zult u het volgende beeld zien:

![ auto_increment ](assets/auto_increment_id.png)

Als de geselecteerde hoofd bijvoorbeeld knooppunt 1 is waar `auto_increment_offset = 1` staat, wordt de id verhoogd met 1. Als een nieuw hoofdknooppunt later wordt geselecteerd, bijvoorbeeld knooppunt 3 waar `auto_increment_offset = 3` , wordt het in plaats daarvan met 3 verhoogd.

## Nuttige koppelingen

Zie in onze documentatie voor ontwikkelaars:

* [ Cloud voor Adobe Commerce > Pro architectuur > Steun en rampenterugwinning ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#backup-and-disaster-recovery)
* [ Wolk voor Adobe Commerce > installeer eerste vereisten: gegevensbestand ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview)
