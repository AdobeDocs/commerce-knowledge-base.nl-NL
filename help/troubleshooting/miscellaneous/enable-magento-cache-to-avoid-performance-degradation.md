---
title: Cache inschakelen om prestatievermindering te voorkomen
description: In dit artikel wordt uitgelegd hoe u een probleem met een trage site kunt oplossen dat wordt veroorzaakt door het uitschakelen van bepaalde Adobe Commerce-cachetypen.
exl-id: e4e5a753-efa3-4552-aaf6-28e44efcfa5b
feature: Cache, Observability
role: Developer
source-git-commit: bd6aa238ff8273c60a4cf5160fb614de6ff00d21
workflow-type: tm+mt
source-wordcount: '292'
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

1. Controleer eerst de status van de Adobe Commerce cache om te zien of dit het probleem is. Voor dit, [ SSH aan uw milieu ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) en stel het volgende bevel in werking:

   ```bash
   php bin/magento cache:status
   ```

   Dit zou de status van elk geheim voorgeheugentype (&quot;0&quot;voor gehandicapte, &quot;1&quot;voor toegelaten) tonen. U kunt deze gegevens ook in het `app/etc/env.php` -bestand opnemen.

1. Onderzoek de gehandicapte geheim voorgeheugentypes. Alle Adobe Commerce cache-typen moeten zijn ingeschakeld, tenzij u alternatieve instructies van Adobe hebt ontvangen. Voor extensies van derden moet geen Adobe Commerce-cache worden uitgeschakeld.
1. Als het onderzoek bevestigt dat sommige geheim voorgeheugentypes door fout gehandicapt zijn, laat hen toe door het volgende bevel voor elk geheim voorgeheugentype in werking te stellen: `php bin/magento cache:enable <your_disabled_cache_type>`

Als er zorgen en/of vragen zijn of een bepaald Adobe Commerce geheim voorgeheugentype kan of zou moeten worden onbruikbaar gemaakt, [ de steun van Adobe Commerce van het contact ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) vragend om aanbevelingen.

## Gerelateerde lezing

Adobe Commerce cache-documentatie in onze ontwikkelaarsdocumentatie:

* [ Adobe Commerce geheim voorgeheugenoverzicht ](https://developer.adobe.com/commerce/frontend-core/guide/caching/)
* [ beheer het geheime voorgeheugen ](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/cli/manage-cache)

Andere mogelijke redenen voor prestatieproblemen en oplossingen voor deze problemen:

* [ maak de output van de Banner van Adobe Commerce onbruikbaar om plaatsprestaties te verbeteren ](https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26909)
* [ MySQL de lijsten zijn te groot ](https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26945)
* [Trage prestaties, langzame en langlopende bekers](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md)
* [Beperkte toegang tot beheerder leidt tot prestatieproblemen](/help/troubleshooting/miscellaneous/restricted-admin-access-causing-performance-issues.md)
