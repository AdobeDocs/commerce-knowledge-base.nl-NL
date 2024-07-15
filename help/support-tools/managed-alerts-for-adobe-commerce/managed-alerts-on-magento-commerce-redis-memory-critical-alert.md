---
title: "Beheerde waarschuwingen over Adobe Commerce: Redis-waarschuwing voor geheugenkritiek"
description: In dit artikel worden stappen beschreven voor het oplossen van problemen wanneer u een Redis-melding ontvangt voor een belangrijke geheugenwaarschuwing voor Adobe Commerce in New Relic. Er is onmiddellijke actie vereist om het probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.
exl-id: 28e1d879-d7ca-4439-8e81-52a1fbf3ecb0
feature: Cache, Categories, Observability, Services, Support, Tools and External Services, Variables
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 0%

---

# Beheerde waarschuwingen voor Adobe Commerce: Redis-waarschuwing voor geheugenkritiek

In dit artikel worden stappen beschreven voor het oplossen van problemen wanneer u een Redis-melding ontvangt voor een belangrijke geheugenwaarschuwing voor Adobe Commerce in New Relic. Er is onmiddellijke actie vereist om het probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd.

![ new_relic_redis_memory_critical.png ](assets/new_relic_redis_memory_critical.png)

## Betrokken producten en versies

Alle versies van Adobe Commerce op de Pro-planarchitectuur van de cloud-infrastructuur

## Probleem

U zult een alarm in New Relic ontvangen als u tot [ Beheerde alarm voor Adobe Commerce ](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) hebt ondertekend en één of meerdere waakzame drempels zijn overschreden. Deze waarschuwingen zijn door de Adobe ontwikkeld om handelaren een standaardreeks waarschuwingen te geven met behulp van inzichten van ondersteuning en engineering.

**<u>doe!</u>**

* Abort om het even welke plaatsing die tot dit alarm wordt gepland wordt ontruimd.
* Zet uw site onmiddellijk in de onderhoudsmodus als uw site helemaal niet reageert of niet meer reageert. Voor stappen verwijzen naar [ Gids van de Installatie > laat of maakt onderhoudswijze ](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#enable-or-disable-maintenance-mode-1) in onze Gids van de Installatie toe onbruikbaar. Zorg ervoor om uw IP aan de Vrijgestelde IP adreslijst toe te voegen om ervoor te zorgen dat u nog tot uw plaats voor het oplossen van problemen kunt toegang hebben. Voor stappen, verwijs naar [ handhaaf de lijst van vrijgestelde IP adressen ](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#maintain-the-list-of-exempt-ip-addresses) in onze Gids van de Installatie.

**<u>niet!</u>**

* Start aanvullende marketingcampagnes die extra pagina&#39;s naar uw site kunnen brengen.
* Voer indexen of extra kranen uit die extra belasting op de CPU of schijf kunnen veroorzaken.
* Voer belangrijke administratieve taken uit (d.w.z. belangrijke acties in de Admin van Commerce zoals gegevensinvoer/uitvoer, het spoelen van media, het redden van categorieën met een groot aantal toegewezen producten, en massa-updates).
* Wis uw cache.

## Oplossing

Volg deze stappen om de oorzaak te identificeren en problemen op te lossen.

**omdat dit een kritiek alarm is, wordt het hoogst geadviseerd u Stap 1 voltooit alvorens u probeert om de kwestie (Stap 2 vanaf) problemen op te lossen.**

1. Controleer of er een Adobe Commerce-ondersteuningsticket bestaat. Voor stappen, verwijs naar [ Spoor uw steunkaartjes ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in onze basis van de steunkennis. De ondersteuning heeft mogelijk al een New Relic-drempelwaardewaarschuwing ontvangen, een ticket gemaakt en aan het probleem gewerkt. Als er geen ticket bestaat, maakt u er een. Het ticket moet de volgende informatie bevatten:

   * Reden van contactpersoon: selecteer &quot;KRITISCHE waarschuwing van New Relic ontvangen&quot;.
   * Beschrijving van de signalering.
   * [ de inherente verbinding van New Relic ](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents/). Dit is inbegrepen in uw [ Beheerde Alarm voor Adobe Commerce ](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).

1. Als geen steunkaartje bestaat, controleer als Redis Gebruikt Geheugen stijgt of door [ te gaan one.newrelic.com ](https://login.newrelic.com) > **Infrastructuur** > **de pagina van de Diensten van de Derden** daalt, selecteer Redis dashboard. Als het stabiel of het verhogen is, [ voorlegt een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om uw cluster te hebben, of verhoog de `maxmemory` grens aan het volgende niveau.
1. Als u niet de oorzaak van verhoogde het geheugenconsumptie van Redis kunt identificeren, herzie recente tendensen om kwesties met recente codeplaatsingen of configuratieveranderingen (bijvoorbeeld, nieuwe klantengroepen en grote veranderingen in de catalogus) te identificeren. U wordt aangeraden de afgelopen zeven dagen van activiteit te controleren op correlaties in codeimplementaties of -wijzigingen.
1. Controleren op onjuiste extensies van derden:

   * Probeer een correlatie te vinden met recent geïnstalleerde extensies van derden en de tijd waarop de uitgave is gestart.
   * Controleer extensies die mogelijk van invloed zijn op de Adobe Commerce-cache en zorgen dat de cache snel groter wordt. Bijvoorbeeld, de blokken van de douanelay-out, het met voeten treden van geheim voorgeheugenfunctionaliteit, en het opslaan van grote hoeveelheden gegevens in geheim voorgeheugen.

1. Als er geen bewijs van verkeerd gedraagt uitbreidingen is, [ installeer recentste flarden om Redis kwesties voor Adobe Commerce op wolkeninfrastructuur ](/help/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues.md) te bevestigen.
1. Als de bovenstaande stappen u niet helpen de bron van de kwestie identificeren of problemen oplossen, denk na toelatend L2 geheime voorgeheugen om netwerkverkeer tussen app en Redis te verminderen. Voor algemene informatie over wat L2 geheime voorgeheugen is, verwijs naar [ L2 caching in de toepassing van Adobe Commerce ](/docs/commerce-operations/configuration-guide/cache/level-two-cache.html) in onze ontwikkelaarsdocumentatie. Ga als volgt te werk om L2-cache in te schakelen voor cloudinfrastructuur:

   * Voer een upgrade uit voor ECE-gereedschappen als de versie onder 2002.1.2 valt.
   * Vorm L2 Geheime voorgeheugen door [ te gebruiken REDIS \_BACKEND veranderlijke ](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) en het bijwerken `.magento.env.yaml` dossier:

   ```yaml
   stage:
       deploy:
           REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
