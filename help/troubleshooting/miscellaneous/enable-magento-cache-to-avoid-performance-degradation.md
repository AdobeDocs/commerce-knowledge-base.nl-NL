---
title: Cache inschakelen om prestatievermindering te voorkomen
description: In dit artikel wordt uitgelegd hoe u een probleem met een trage site kunt oplossen dat wordt veroorzaakt door het uitschakelen van bepaalde Adobe Commerce-cachetypen.
exl-id: e4e5a753-efa3-4552-aaf6-28e44efcfa5b
feature: Cache, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Cache inschakelen om prestatievermindering te voorkomen

In dit artikel wordt uitgelegd hoe u een probleem met een trage site kunt oplossen dat wordt veroorzaakt door het uitschakelen van bepaalde Adobe Commerce-cachetypen.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur 2.2.x, 2.3.x
* Adobe Commerce op locatie 2.2.x, 2.3.x

## Probleem

U merkt dat de prestaties achteruitgaan. De pagina Uitchecken wordt bijvoorbeeld langzaam geladen of de waarde van de Apdex neemt af in New Relic.

## Oorzaak

Een reden voor prestatievermindering kan zijn dat bepaalde Adobe Commerce-cachetypen zijn uitgeschakeld.

## Oplossing

1. Controleer eerst de status van de Adobe Commerce cache om te zien of dit het probleem is. Hiervoor [SSH voor uw omgeving](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) en voer de volgende opdracht uit:

   ```bash
   php bin/magento cache:status
   ```

   Dit zou de status van elk geheim voorgeheugentype (&quot;0&quot;voor gehandicapte, &quot;1&quot;voor toegelaten) tonen. U kunt deze gegevens ook in het dialoogvenster `app/etc/env.php` bestand.

1. Onderzoek de gehandicapte geheim voorgeheugentypes. Alle Adobe Commerce-cachetypen moeten zijn ingeschakeld, tenzij u alternatieve instructies van de Adobe hebt ontvangen. Voor extensies van derden moet geen Adobe Commerce-cache worden uitgeschakeld.
1. Als het onderzoek bevestigt dat sommige geheim voorgeheugentypes door fout gehandicapt zijn, laat hen toe door het volgende bevel voor elk geheim voorgeheugentype in werking te stellen: `php bin/magento cache:enable <your_disabled_cache_type>`

Als er bezorgdheid en/of vragen zijn of een bepaald Adobe Commerce-cachetype kan of moet worden uitgeschakeld, [contact opnemen met Adobe Commerce-ondersteuning](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) vragen om aanbevelingen.

## Gerelateerde lezing

Adobe Commerce cache-documentatie in onze ontwikkelaarsdocumentatie:

* [Overzicht Adobe Commerce cache](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/cache_for_frontdevs.html)
* [De cache beheren](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cache.html)

Andere mogelijke redenen voor prestatieproblemen en oplossingen voor deze problemen:

* [Uitvoer van Adobe Commerce Banner uitschakelen om de prestaties van de site te verbeteren](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md)
* [MySQL-tabellen zijn te groot](/help/troubleshooting/database/mysql-tables-are-too-large.md)
* [Trage prestaties, langzame en langlopende bekers](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md)
* [Beperkte toegang tot beheerder leidt tot prestatieproblemen](/help/troubleshooting/miscellaneous/restricted-admin-access-causing-performance-issues.md)
