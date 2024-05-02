---
title: Hoe controleert u waarom? [!DNL cron] was uitgeschakeld
description: Dit artikel biedt oplossingen voor het oplossen van problemen voor problemen met cron in Adobe Commerce op producten van de cloudinfrastructuur.
feature: Configuration
role: Developer
exl-id: d4d4a28d-3afa-4379-afc1-bc6250717784
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Hoe controleert u waarom? [!DNL cron] was uitgeschakeld

Dit artikel biedt oplossingen voor probleemoplossing voor problemen met [!DNL cron] in Adobe Commerce over wolkeninfrastructuurproducten.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur, alle versies

## Probleem

## De volgende symptomen zijn: [!DNL cron] problemen:

U hebt gemerkt dat uw [!DNL cron] was niet aan de gang.
U ziet bijvoorbeeld de volgende regels in het dialoogvenster `app/etc/env.php` bestand:

```'cron' =>
  array (
    'enabled' => 0
  ),
```

Een lege array zou betekenen dat de [!DNL cron] is **enabled**:

```'cron' =>
  array (
  ),
```

## Oorzaken

Er zijn verschillende redenen waarom de [!DNL cron] is momenteel niet actief:

1. De [!DNL cron] was uitgeschakeld omdat deze was overgeslagen [!DNL OpCache] instellingen.
1. Het infrastructuurteam heeft uw [!DNL cron], omdat dit ertoe leidde dat uw site traag ging presteren/verdwijnen.
1. De [!DNL cron] werd niet opnieuw ingeschakeld omdat uw implementatie is mislukt.

Zie een van de volgende secties voor een oplossing van uw probleem.

## Oplossingen

### Oplossing voor gemiste [!DNL OpCache] instellingen {#solution-missed-opcache-settings}

Zie [[!DNL Cron] gestopt wegens verkeerd gevormd of mist [!DNL OpCache] instellingen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/crons-blocked-running-missing-opache-settings) in onze Commerce-kennisbasis.

### Oplossing voor gehandicapten door het infrastructuurteam {#solution-disabled-by-infrastructure-team}

1. Controleer uw vorige ondersteuningstickets waarin uw site niet beschikbaar was of waarin niet werd gereageerd.
1. Controleer vervolgens of het infrastructuurteam heeft aangegeven het uit te schakelen.
1. Controleer of u de problemen/zorgen hebt opgelost die door het infrastructuurteam naar voren zijn gebracht.
1. Een [Ondersteuningsverzoek](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) als u verdere hulp nodig hebt om het [!DNL cron] en uitleggen hoe u de problemen hebt aangepakt die het infrastructuurteam heeft aangegeven.

### Oplossing voor implementatie mislukt {#solution-deployment-failed}

Controleer de implementatielogboeken:

* [Logbestanden weergeven en beheren](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) in onze Commerce on Cloud Infrastructure Guide.
* [Implementatielogbestand controleren als de gebruikersinterface van Cloud *`log snipped`* fout](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error) in onze Commerce-kennisbasis.

1. Als de implementatie tijdens de `setup:upgrade` de [!DNL cron] niet opnieuw ingeschakeld zijn.
Bijvoorbeeld: u ziet deze lijn in het plaatsingslogboek:

   ```The command "/bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade --keep-generated --ansi --no-interaction  | tee -a /app/$<project_id>/var/log/install_upgrade.log"" failed. Cache types config flushed successfully```

1. Anders, zou de plaatsing tijdens één of ander ander stadium kunnen ontbroken hebben. Controleer het implementatielogboek en controleer of beide regels worden weergegeven (zie het onderstaande voorbeeld). Als u niet beide lijnen gelijkaardig aan dit in het logboek ziet, betekent het dat [!DNL cron] is niet opnieuw ingeschakeld:

   ```  [2024-03-06T10:55:39.345564+00:00] INFO: Disable cron```<br>
...<br>
   ```  [2024-02-07T10:50:09.579005+00:00] INFO: Enable cron```

**Een [Ondersteuningsverzoek](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) als u verdere hulp nodig hebt.**
