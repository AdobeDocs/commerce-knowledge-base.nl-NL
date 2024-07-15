---
title: 'Beheerde waarschuwingen voor Adobe Commerce: waarschuwing voor geheugenbeschadiging'
description: 'Dit artikel bevat stappen voor het oplossen van problemen wanneer u een waarschuwingsbericht van Redis voor Adobe Commerce in New Relic ontvangt. Er is onmiddellijke actie vereist om het probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd:'
exl-id: b7867a42-3817-4cb4-93cf-d69acee33a41
feature: Categories, Marketing Tools, Observability, Services, Support, Tools and External Services, Variables
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Beheerde waarschuwingen voor Adobe Commerce: waarschuwing voor opnieuw verzonden geheugen

Dit artikel bevat stappen voor het oplossen van problemen wanneer u een waarschuwingsbericht van Redis voor Adobe Commerce in New Relic ontvangt. Er is onmiddellijke actie vereist om het probleem op te lossen. De waarschuwing ziet er ongeveer als volgt uit, afhankelijk van het waarschuwingsberichtkanaal dat u hebt geselecteerd:

![ new_relic_redis_memory_warning.png ](assets/new_relic_redis_memory_warning.png)

## Betrokken producten en versies

Alle versies van Adobe Commerce op cloudinfrastructuur Pro plannen.

## Probleem

U zult een alarm in New Relic ontvangen als u tot [ Beheerde alarm voor Adobe Commerce ](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) hebt ondertekend en één of meerdere waakzame drempels zijn overschreden. Deze waarschuwingen zijn door de Adobe ontwikkeld om handelaren een standaardreeks waarschuwingen te geven met behulp van inzichten van ondersteuning en engineering.

**<u>doe!</u>**

* U wordt aangeraden de geplande implementatie af te breken totdat deze waarschuwing wordt gewist.
* Als uw site niet reageert of volledig reageert, zet u uw site onmiddellijk in de onderhoudsmodus. Voor stappen, verwijs naar [ Gids van de Installatie > laat of maakt onderhoudswijze ](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#enable-or-disable-maintenance-mode-1) in onze Gids van de Installatie toe onbruikbaar.
* Zorg ervoor om uw IP aan de Vrijgestelde IP adreslijst toe te voegen om ervoor te zorgen dat u nog tot uw plaats voor het oplossen van problemen kunt toegang hebben. Voor stappen, verwijs naar [ handhaaf de lijst van vrijgestelde IP adressen ](/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html#maintain-the-list-of-exempt-ip-addresses) in onze Gids van de Installatie.

**<u>niet!</u>**

* Start aanvullende marketingcampagnes die extra pagina&#39;s naar uw site kunnen brengen.
* Voer indexen of extra kranen uit die extra belasting op de CPU of schijf kunnen veroorzaken.
* Voer belangrijke administratieve taken uit (d.w.z. belangrijke acties in Commerce Admin zoals invoer/uitvoer van gegevens, het spoelen van media, het redden van categorieën met een groot aantal toegewezen producten, en massa-updates).
* Wis uw cache.

## Oplossing

Volg deze stappen om de oorzaak te identificeren en problemen op te lossen.

1. Controle als Redis Gebruikt Geheugen stijgt of vermindert door [ te gaan one.newrelic.com ](https://login.newrelic.com/login) > **Infrastructuur** > **de pagina van de diensten van de Derde**, selecteert Redis dashboard. Als het stabiel of het verhogen is, [ voorlegt een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om uw cluster te hebben, of verhoog de `maxmemory` grens aan het volgende niveau.
1. Als u niet de oorzaak van verhoogde het geheugenconsumptie van Redis kunt identificeren, herzie recente tendensen om kwesties met recente codeplaatsingen of configuratieveranderingen (bijvoorbeeld, nieuwe klantengroepen en grote veranderingen in de catalogus) te identificeren. U wordt aangeraden de afgelopen zeven dagen van activiteit te controleren op correlaties in codeimplementaties of -wijzigingen.
1. Controleren op onjuiste extensies van derden:
   * Probeer een correlatie te vinden met recent geïnstalleerde extensies van derden en de tijd waarop de uitgave is gestart.
   * Controleer extensies die mogelijk van invloed zijn op de Adobe Commerce-cache en zorgen dat de cache snel groter wordt. Bijvoorbeeld, de blokken van de douanelay-out, het met voeten treden van geheim voorgeheugenfunctionaliteit, en het opslaan van grote hoeveelheden gegevens in geheim voorgeheugen.
1. Als er geen bewijs van verkeerd gedraagt uitbreidingen is, [ installeer recentste flarden om Redis kwesties voor Adobe Commerce op wolkeninfrastructuur ](/help/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues.md) te bevestigen. Als de bovenstaande stappen u niet helpen de bron van de kwestie identificeren of problemen oplossen, denk na toelatend L2 geheime voorgeheugen om netwerkverkeer tussen app en Redis te verminderen. Voor algemene informatie over wat L2 geheim voorgeheugen is, verwijs naar [ L2 caching in de toepassing van Adobe Commerce ](/docs/commerce-operations/configuration-guide/cache/level-two-cache.html) in onze Gids van de Configuratie. Ga als volgt te werk om L2-cache in te schakelen voor cloudinfrastructuur:
   * Voer een upgrade uit voor ECE-gereedschappen als de versie onder 2002.1.2 valt.
   * Vorm L2 Geheime voorgeheugen door [ te gebruiken REDIS \_BACKEND veranderlijke ](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) en het bijwerken `.magento.env.yaml` dossier:

   ```yaml
   stage:
      deploy:
          REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
