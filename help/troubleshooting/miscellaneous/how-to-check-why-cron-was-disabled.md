---
title: Hoe te om te controleren waarom  [!DNL cron]  gehandicapt was
description: Dit artikel biedt oplossingen voor het oplossen van problemen voor problemen met cron in Adobe Commerce op producten van de cloudinfrastructuur.
feature: Configuration
role: Developer
exl-id: d4d4a28d-3afa-4379-afc1-bc6250717784
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Controleren waarom [!DNL cron] is uitgeschakeld

Dit artikel biedt oplossingen voor het oplossen van problemen voor problemen met [!DNL cron] in Adobe Commerce met producten voor cloudinfrastructuur.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur, alle versies

## Probleem

## Hieronder volgen de symptomen van [!DNL cron] -problemen:

U hebt gemerkt dat uw [!DNL cron] niet actief was.
U ziet bijvoorbeeld de volgende regels in het `app/etc/env.php` -bestand:

```'cron' =>
  array (
    'enabled' => 0
  ),
```

Een lege serie zou betekenen dat [!DNL cron] **&#x200B;**&#x200B;wordt toegelaten:

```'cron' =>
  array (
  ),
```

## Oorzaken

Er zijn verschillende redenen waarom [!DNL cron] momenteel niet actief is:

1. [!DNL cron] is uitgeschakeld omdat de [!DNL OpCache] -instellingen zijn overgeslagen.
1. Het infrastructuurteam heeft uw [!DNL cron] uitgeschakeld, omdat dit ertoe leidde dat uw site slecht of niet kon functioneren.
1. [!DNL cron] is niet opnieuw ingeschakeld omdat uw implementatie is mislukt.

Zie een van de volgende secties voor een oplossing van uw probleem.

## Oplossingen

### Oplossing voor gemiste [!DNL OpCache] -instellingen {#solution-missed-opcache-settings}

Zie [[!DNL Cron]  gestopt toe te schrijven aan misconfigured of ontbrekende  [!DNL OpCache]  montages ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/crons-blocked-running-missing-opache-settings) in onze de kennisbasis van Commerce.

### Oplossing voor gehandicapten door het infrastructuurteam {#solution-disabled-by-infrastructure-team}

1. Controleer uw vorige ondersteuningstickets waarin uw site niet beschikbaar was of waarin niet werd gereageerd.
1. Controleer vervolgens of het infrastructuurteam heeft aangegeven het uit te schakelen.
1. Controleer of u de problemen/zorgen hebt opgelost die door het infrastructuurteam naar voren zijn gebracht.
1. Verzend het verzoek van de a [ Steun ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) als u verdere hulp nodig hebt om [!DNL cron] re-toe te laten en te verklaren hoe u de kwesties hebt gericht die het team van de Infrastructuur verwees.

### Oplossing voor implementatie mislukt {#solution-deployment-failed}

Controleer de implementatielogboeken:

* [ Mening en beheer logboeken ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) in onze Commerce op de Gids van de Infrastructuur van de Wolk.
* [ Controlerend plaatsingslogboek als de UI van de Wolk *`log snipped`* fout ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error) in onze kennisbasis van Commerce heeft.

1. Als de implementatie tijdens de stap `setup:upgrade` is mislukt, is [!DNL cron] niet opnieuw ingeschakeld.
Bijvoorbeeld: u ziet deze lijn in het plaatsingslogboek:

   ```The command "/bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade --keep-generated --ansi --no-interaction  | tee -a /app/$<project_id>/var/log/install_upgrade.log"" failed. Cache types config flushed successfully```

1. Anders, zou de plaatsing tijdens één of ander ander stadium kunnen ontbroken hebben. Controleer het implementatielogboek en controleer of beide regels worden weergegeven (zie het onderstaande voorbeeld). Als beide regels niet op deze manier worden weergegeven in het logbestand, betekent dit dat [!DNL cron] niet opnieuw is ingeschakeld:

   ```  [2024-03-06T10:55:39.345564+00:00] INFO: Disable cron```<br>
... <br>
   ```  [2024-02-07T10:50:09.579005+00:00] INFO: Enable cron```

**leg het verzoek van de a [ Steun ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) voor als u verdere hulp nodig hebt.**
