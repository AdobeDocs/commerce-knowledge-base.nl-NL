---
title: Uitsnijding oplossen
description: Dit artikel biedt oplossingen voor het oplossen van problemen voor problemen met cron in Adobe Commerce on-premisse producten.
exl-id: e69a4fb3-731b-449e-a815-c33cd2faa567
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# Uitsnijding oplossen

Dit artikel biedt oplossingen voor het oplossen van problemen voor problemen met cron in Adobe Commerce on-premisse producten.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problemen

## Hieronder volgen de symptomen van problemen met de borst:

* De update of upgrade wordt nooit uitgevoerd. De status blijft `pending` ingeschakeld.
* Er wordt een foutbericht weergegeven over de PHP-instelling `$HTTP_RAW_POST_DATA` , ook al is deze correct ingesteld.
* De gereedheidscontrole voor uitsnijden mislukt. Mogelijke fouten zijn onder andere niet-schrijfbare paden en het uitsnijden is niet ingesteld. Hier volgt een voorbeeld:

  ![ upgr-tshoot-no-cron2.png ](assets/upgr-tshoot-no-cron2.png)

* De PHP gereedheidscontrole geeft de PHP versie niet weer zoals de volgende afbeelding laat zien.

  ![ Screen_Shot_2019-08-29_at_1.36.08_PM.png ](assets/Screen_Shot_2019-08-29_at_1.36.08_PM.png)

* De volgende fout wordt weergegeven in Commerce Admin:

  ![ compman-cron-not-running.png ](assets/compman-cron-not-running.png)

Om de fout te zien, zou u **Berichten van het Systeem** bij de bovenkant van het venster als volgt kunnen moeten klikken:

![ compman_sys-messages.png ](assets/compman_sys-messages.png)

## Onderzoek om de oorzaak te vinden {#check-your-existing-crontab}

In deze sectie wordt besproken hoe u kunt zien of de uitsnede momenteel wordt uitgevoerd en of deze op de juiste wijze is ingesteld.

Ga als volgt te werk om te controleren of de tab is ingesteld:

1. Login aan uw server van het Magento als, of schakelaar aan, de [ eigenaar van het het dossiersysteem van het Magento ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/prerequisites/file-system/overview).
1. Controleer of het volgende bestand bestaat:    `bash    ls -al <magento_root>/var/.setup_cronjob_status`. Als het bestand bestaat, is het uitsnijden in het verleden gelukt. Als het dossier *niet* bestaat, of hebt u nog niet geïnstalleerd Magento of de kroon loopt niet. Ga in beide gevallen verder met de volgende stap.
1. Meer informatie over uitsnijden. Als gebruiker met `root` voorrechten, ga het volgende bevel in:    `bash    crontab -u <Magento file system owner name> -l` . Bijvoorbeeld op CentOS `bash    crontab -u magento_user -l` .  Als er geen tab voor de gebruiker is ingesteld, wordt het volgende bericht weergegeven:    `terminal    no crontab for magento_user`. Uw tab geeft het volgende weer:

   * Wat gebruikt PHP binair u (in sommige gevallen, hebt u meer dan één)
   * Welk Magento snijdt manuscripten uit u loopt (in het bijzonder, de wegen aan die manuscripten)
   * Waar uw uitsnijdlogs zich bevinden

Zie een van de volgende secties voor een oplossing van uw probleem.

## Oplossingen

### Oplossing voor crontab niet ingesteld {#solution-crontab-not-set-up}

Om uw kroonbanen te verifiëren worden opstelling behoorlijk, zie [ banen van de opstelling cron ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/next-steps/configuration).

### Oplossing voor uitsnede die wordt uitgevoerd vanuit onjuist PHP binair {#solution-cron-running-from-incorrect-php-binary}

Als uw uitsnijdtaak een binair PHP-bestand gebruikt dat afwijkt van de insteekmodule voor de webserver, kunnen fouten in de PHP-instellingen worden weergegeven. Om dit probleem op te lossen, stelt u identieke PHP-instellingen in voor zowel de PHP opdrachtregel als de PHP webserver plug-in.

Voor meer informatie over PHP montages, zie [ Vereiste PHP montages ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/prerequisites/php-settings) in onze ontwikkelaarsdocumentatie.

### Oplossing voor uitsnijden met fouten {#solution-cron-running-with-errors}

Probeer elke opdracht handmatig uit te voeren, omdat de opdracht nuttige foutberichten kan weergeven. Zie [ de banen van de opstelling cron ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/next-steps/configuration).

>[!NOTE]
>
>U moet kroon minstens *tweemaal* voor de uit te voeren baan in werking stellen; de eerste keer om banen in rij te plaatsen, de tweede keer om de banen uit te voeren.
