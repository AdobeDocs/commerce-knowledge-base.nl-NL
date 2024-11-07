---
title: Trage prestaties, langzame en langlopende bekers
description: In dit artikel wordt beschreven hoe u problemen met de siteprestaties kunt oplossen en hoe u de werking en het vastlopen van crons kunt vertragen die worden veroorzaakt door platte tabellen en indexeerders die zijn ingeschakeld.
exl-id: a78ca3c3-85b4-40a1-a693-4703dd3ef4b5
feature: Best Practices, Cache, Categories, Catalog Management
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Trage prestaties, langzame en langlopende bekers

>[!WARNING]
>
>Aangezien bepaalde extensies alleen werken met platte tabellen, is er bij elke Adobe Commerce-versie een risico als u platte tabellen uitschakelt. Als u weet dat u sommige uitbreidingen hebt die de Platte indexeerders van de Catalogus gebruiken, kunt u dat in overweging moeten nemen wanneer het plaatsen van die waarden aan &quot; *Nr* &quot;.

Dit artikel beschrijft hoe te om de kwesties van plaatsprestaties op te lossen en het vertragen van en vastgezette kronen die door [ vlakke lijsten en indexeerders ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/catalog-flat) worden veroorzaakt die zijn toegelaten.

BETROKKEN PRODUCTEN EN VERSIES

* Adobe Commerce op cloudinfrastructuur 2.1.x en hoger
* Adobe Commerce op locatie 2.1.x en hoger
* Magento Open Source 2.1.x en hoger

## Probleem

Vlakke indexen kunnen:

* Zware problemen met het laden van SQL en de prestaties van de site.
* Langlopende en geplakte manen.

## Oorzaak

Vlakke tabellen en indexeertekens ingeschakeld.

## Oplossing {#solution}

Vanaf Adobe Commerce en Magento Open Source 2.1.x en hoger is het gebruik van een platte catalogus niet langer de beste werkwijze en wordt het gebruik ervan afgeraden. Het is bekend dat voortdurend gebruik van deze functie prestatievermindering en andere indexeringsproblemen kan veroorzaken. De vlakke catalogus uitschakelen:

1. In Admin, navigeer aan **Opslag** > **Montages** > **Configuratie**.
1. In het paneel op de linkerzijde onder **Catalogus**, kies **Catalogus**.
1. Breid de **sectie Storefront** uit, en doe het volgende:
   * Plaats **de Vlakke Categorie van de Catalogus van het Gebruik** aan *Nr*.
   * Plaats **het Platte Product van de Catalogus van het Gebruik** aan *Nr*.
1. Wanneer volledig, klik **sparen Config**. Vernieuw vervolgens de cache wanneer hierom wordt gevraagd.
1. Cache leegmaken door uit te voeren `php bin/magento cache:flush`.

Als u niet de **Vlakke Categorie van de Catalogus van het Gebruik** kunt veranderen en **het Vlakke Product van de Catalogus van het Gebruik** aan *Nr* omdat de opties uit grijs zijn, maak vlakke indexen in `app/etc/config.php` onbruikbaar:

1. Voer deze opdracht uit om ervoor te zorgen dat alle indexen zijn ingesteld op Bijwerken volgens schema: `php bin/magento indexer:set-mode schedule` .
1. Bewerk `app/etc/config.php` en zoek de regels met `flat_catalog_product` en `flat_catalog_category` - verander deze van 1 in 0 om ze uit te schakelen.
1. De opdracht uitvoeren `php bin/magento app:config:import`
1. Voer deze opdracht uit om te bevestigen dat de vlakke indexen zijn uitgeschakeld: `php        bin/magento indexer:status`.
1. Cache leegmaken door uit te voeren `php bin/magento cache:flush`.

## Gerelateerde informatie

[ het Terugstellen vastgezette banen van Adobe Commerce cron manueel op Wolk ](/help/how-to/general/reset-stuck-magento-cron-jobs-manually-on-cloud.md) in onze basis van steunkennis.
