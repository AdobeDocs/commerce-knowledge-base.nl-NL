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

![new_relic_redis_memory_kritiek.png](assets/new_relic_redis_memory_critical.png)

## Betrokken producten en versies

Alle versies van Adobe Commerce op de Pro-planarchitectuur van de cloud-infrastructuur

## Probleem

Je ontvangt een bericht in New Relic als je je hebt aangemeld bij [Beheerde waarschuwingen voor Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) en een of meer alarmdrempels zijn overschreden. Deze waarschuwingen zijn door de Adobe ontwikkeld om handelaren een standaardreeks waarschuwingen te geven met behulp van inzichten van ondersteuning en engineering.

**<u>Doe het!</u>**

* Abort om het even welke plaatsing die tot dit alarm wordt gepland wordt ontruimd.
* Zet uw site onmiddellijk in de onderhoudsmodus als uw site helemaal niet reageert of niet meer reageert. Zie voor stappen [Installatiegids > Onderhoudsmodus in- of uitschakelen](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#enable-or-disable-maintenance-mode-1) in onze installatiehandleiding. Zorg ervoor om uw IP aan de Vrijgestelde IP adreslijst toe te voegen om ervoor te zorgen dat u nog tot uw plaats voor het oplossen van problemen kunt toegang hebben. Raadpleeg voor stappen [Handhaaf de lijst van vrijgestelde IP adressen](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#maintain-the-list-of-exempt-ip-addresses) in onze installatiehandleiding.

**<u>Niet doen!</u>**

* Start aanvullende marketingcampagnes die extra pagina&#39;s naar uw site kunnen brengen.
* Voer indexen of extra kranen uit die extra belasting op de CPU of schijf kunnen veroorzaken.
* Voer belangrijke administratieve taken uit (d.w.z. belangrijke acties in de Admin van Commerce zoals gegevensinvoer/uitvoer, het spoelen van media, het redden van categorieën met een groot aantal toegewezen producten, en massa-updates).
* Wis uw cache.

## Oplossing

Volg deze stappen om de oorzaak te identificeren en problemen op te lossen.

**Omdat dit een kritieke alarm is, wordt het hoogst geadviseerd u Stap 1 voltooit alvorens u probeert om de kwestie (Stap 2 vanaf) problemen op te lossen.**

1. Controleer of er een Adobe Commerce-ondersteuningsticket bestaat. Raadpleeg voor stappen [Volg uw ondersteuningstickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) in onze kennisbasis voor ondersteuning. De ondersteuning heeft mogelijk al een New Relic-drempelwaardewaarschuwing ontvangen, een ticket gemaakt en aan het probleem gewerkt. Als er geen ticket bestaat, maakt u er een. Het ticket moet de volgende informatie bevatten:

   * Reden van contactpersoon: selecteer &quot;KRITISCHE waarschuwing van New Relic ontvangen&quot;.
   * Beschrijving van de signalering.
   * [Relatie met New Relic-incident](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents/). Dit is inbegrepen in uw [Beheerde waarschuwingen voor Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).

1. Als er geen ondersteuningsticket bestaat, controleert u of het gebruikte geheugen van Redis toeneemt of afneemt door naar [one.newrelic.com](https://login.newrelic.com) > **Infrastructuur** > **Diensten van derden** selecteert u het Redis-dashboard. Indien het stabiel is of toeneemt, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om uw cluster te vergroten, of `maxmemory` beperken tot het volgende niveau.
1. Als u niet de oorzaak van verhoogde het geheugenconsumptie van Redis kunt identificeren, herzie recente tendensen om kwesties met recente codeplaatsingen of configuratieveranderingen (bijvoorbeeld, nieuwe klantengroepen en grote veranderingen in de catalogus) te identificeren. U wordt aangeraden de afgelopen zeven dagen van activiteit te controleren op correlaties in codeimplementaties of -wijzigingen.
1. Controleren op onjuiste extensies van derden:

   * Probeer een correlatie te vinden met recent geïnstalleerde extensies van derden en de tijd waarop de uitgave is gestart.
   * Controleer extensies die mogelijk van invloed zijn op de Adobe Commerce-cache en zorgen dat de cache snel groter wordt. Bijvoorbeeld, de blokken van de douanelay-out, het met voeten treden van geheim voorgeheugenfunctionaliteit, en het opslaan van grote hoeveelheden gegevens in geheim voorgeheugen.

1. Indien er geen aanwijzingen zijn dat de verlengingen onjuist zijn, [Nieuwste patches installeren om Redis-problemen voor Adobe Commerce op cloudinfrastructuur te verhelpen](/help/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues.md).
1. Als de bovenstaande stappen u niet helpen de bron van de kwestie identificeren of problemen oplossen, denk na toelatend L2 geheime voorgeheugen om netwerkverkeer tussen app en Redis te verminderen. Voor algemene informatie over wat L2 cache is, raadpleegt u [L2 caching in de Adobe Commerce toepassing](/docs/commerce-operations/configuration-guide/cache/level-two-cache.html) in onze ontwikkelaarsdocumentatie. Ga als volgt te werk om L2-cache in te schakelen voor cloudinfrastructuur:

   * Voer een upgrade uit voor ECE-gereedschappen als de versie onder 2002.1.2 valt.
   * L2 Cache configureren door [REDIS\_BACKEND-variabele gebruiken](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) en bijwerken `.magento.env.yaml` bestand:

   ```yaml
   stage:
       deploy:
           REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
