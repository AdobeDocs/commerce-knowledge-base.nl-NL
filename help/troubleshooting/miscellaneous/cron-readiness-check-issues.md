---
title: Problemen met gereedheid voor uitsnijden
description: '''Dit artikel biedt oplossingen voor problemen met de gereedheid voor uitsnijden. Hieronder volgen de symptomen van problemen met de kron: "'
exl-id: 1f2cee2c-98ad-4cf5-af16-d736fced2a15
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Problemen met gereedheid voor uitsnijden

Dit artikel biedt oplossingen voor problemen met gereedheid voor uitsnijden. Hieronder volgen de symptomen van problemen met de borst:

* Er wordt een foutbericht weergegeven over de PHP-instelling `$HTTP_RAW_POST_DATA` , ook al is deze correct ingesteld.
* De PHP gereedheidscontrole geeft de PHP versie niet weer zoals de volgende afbeelding laat zien:
  ![ upgr-tshoot-no-cron.png ](assets/upgr-tshoot-no-cron.png)
* De volgende fout wordt weergegeven in Commerce Admin:
  ![ compman-cron-not-running.png ](assets/compman-cron-not-running.png)
Om de fout te zien, zou u **Berichten van het Systeem** bij de bovenkant van het venster als volgt kunnen moeten klikken:
  ![ compman_sys-messages.png ](assets/compman_sys-messages.png)

## De bestaande tab controleren {#check-your-existing-crontab}

In deze sectie wordt besproken hoe u kunt zien of de uitsnede momenteel wordt uitgevoerd en of deze op de juiste wijze is ingesteld.

Om te controleren of uw tab is ingesteld:

1. Login aan uw server van Commerce als, of schakelaar aan, de [ eigenaar van het het dossiersysteem van het Magento ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/file-system/overview).
1. Controleer of het volgende bestand bestaat: `$ ls -al <magento_root>/var/.setup_cronjob_status` . Als het bestand bestaat, is het uitsnijden in het verleden gelukt. Als het dossier *niet* bestaat, of hebt u nog niet Adobe Commerce geïnstalleerd of bouwt loopt niet. Ga in beide gevallen verder met de volgende stap.
1. Meer informatie over uitsnijden. Als gebruiker met `root` bevoegdheden voert u de volgende opdracht in: `$ crontab -u <Magento file system owner name> -l` . Bijvoorbeeld op CentOS `$ crontab -u magento_user -l` . Als er geen tab voor de gebruiker is ingesteld, wordt het volgende bericht weergegeven:    `no crontab for magento_user`. Uw tab geeft het volgende weer:
   * Wat gebruikt PHP binair u (in sommige gevallen, hebt u meer dan één)
   * Welke Adobe Commerce-scripts worden uitgevoerd (in het bijzonder de paden naar die scripts)
   * Waar uw uitsnijdlogs zich bevinden

   Zie een van de volgende secties voor een oplossing van uw probleem.

## Oplossing: crontab niet ingesteld {#solution-crontab-not-set-up}

Om uw kroonbanen te verifiëren worden opstelling behoorlijk, zie [ banen van de opstelling cron ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/next-steps/configuration) in onze ontwikkelaarsdocumentatie.

## Oplossing: uit onjuist binair PHP-bestand doorsnijden {#solution-cron-running-from-incorrect-php-binary}

Als uw uitsnijdtaak een binair PHP-bestand gebruikt dat afwijkt van de insteekmodule voor de webserver, kunnen fouten in de PHP-instellingen worden weergegeven. Om dit probleem op te lossen, stelt u identieke PHP-instellingen in voor zowel de PHP opdrachtregel als de PHP webserver plug-in.

Voor meer informatie over PHP montages, zie [ Vereiste PHP montages ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings) in onze ontwikkelaarsdocumentatie.

## Oplossing: fout bij uitvoeren {#solution-cron-running-with-errors}

Probeer elke opdracht handmatig uit te voeren, omdat de opdracht nuttige foutberichten kan weergeven. Zie [ de banen van de opstelling cron ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/next-steps/configuration) in onze ontwikkelaarsdocumentatie.

>[!NOTE]
>
>U moet kroon minstens *tweemaal* voor de uit te voeren baan in werking stellen; de eerste keer om banen in rij te plaatsen, de tweede keer om de banen uit te voeren.
