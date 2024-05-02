---
title: Uitsnijding oplossen
description: Dit artikel biedt oplossingen voor het oplossen van problemen voor problemen met cron in Adobe Commerce on-premisse producten.
exl-id: e69a4fb3-731b-449e-a815-c33cd2faa567
feature: Configuration
role: Developer
source-git-commit: b6a79bcff3d757d40e7070182d8853a37960a782
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Uitsnijding oplossen

Dit artikel biedt oplossingen voor het oplossen van problemen voor problemen met cron in Adobe Commerce on-premisse producten.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problemen

## Hieronder volgen de symptomen van problemen met de borst:

* Uw update of upgrade wordt nooit uitgevoerd; deze blijft in een `pending` status.
* Een foutbericht over de [PHP](https://glossary.magento.com/php) instellen `$HTTP_RAW_POST_DATA` wordt weergegeven, ook al is de instelling correct ingesteld.
* De gereedheidscontrole voor uitsnijden mislukt. Mogelijke fouten zijn onder andere niet-schrijfbare paden en het uitsnijden is niet ingesteld. Hier volgt een voorbeeld:

  ![upgr-tshoot-no-cron2.png](assets/upgr-tshoot-no-cron2.png)

* De PHP gereedheidscontrole geeft de PHP versie niet weer zoals de volgende afbeelding laat zien.

  ![Screen_Shot_2019-08-29_at_1.36.08_PM.png](assets/Screen_Shot_2019-08-29_at_1.36.08_PM.png)

* De volgende fout wordt weergegeven in Commerce Admin:

  ![compman-cron-not-running.png](assets/compman-cron-not-running.png)

Om de fout te zien, zou u kunnen moeten klikken **Systeemberichten** boven aan het venster als volgt:

![compman_sys-messages.png](assets/compman_sys-messages.png)

## Onderzoek om de oorzaak te vinden {#check-your-existing-crontab}

In deze sectie wordt besproken hoe u kunt zien of de uitsnede momenteel wordt uitgevoerd en of deze op de juiste wijze is ingesteld.

Ga als volgt te werk om te controleren of de tab is ingesteld:

1. Meld u aan bij de server van het Magento als of schakel over naar de [Bestandseigenaar Magento](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html).
1. Controleer of het volgende bestand bestaat:    `bash    ls -al <magento_root>/var/.setup_cronjob_status`. Als het bestand bestaat, is het uitsnijden in het verleden gelukt. Als het bestand *niet* bestaat, of u hebt nog niet geïnstalleerd Magento of kruin loopt niet. Ga in beide gevallen verder met de volgende stap.
1. Meer informatie over uitsnijden. Als gebruiker met `root` rechten, voert u de volgende opdracht in:    `bash    crontab -u <Magento file system owner name> -l`. Bijvoorbeeld op CentOS `bash    crontab -u magento_user -l`.  Als er geen tab voor de gebruiker is ingesteld, wordt het volgende bericht weergegeven:    `terminal    no crontab for magento_user`. Uw tab geeft het volgende weer:

   * Wat gebruikt PHP binair u (in sommige gevallen, hebt u meer dan één)
   * Welk Magento snijdt manuscripten uit u loopt (in het bijzonder, de wegen aan die manuscripten)
   * Waar uw uitsnijdlogs zich bevinden

Zie een van de volgende secties voor een oplossing van uw probleem.

## Oplossingen

### Oplossing voor crontab niet ingesteld {#solution-crontab-not-set-up}

Als u wilt controleren of de uitsnijdtaken correct zijn ingesteld, raadpleegt u [Uitsnijdtaken instellen](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron).

### Oplossing voor uitsnede die wordt uitgevoerd vanuit onjuist PHP binair {#solution-cron-running-from-incorrect-php-binary}

Als uw uitsnijdtaak een binair PHP-bestand gebruikt dat afwijkt van de insteekmodule voor de webserver, kunnen fouten in de PHP-instellingen worden weergegeven. Om dit probleem op te lossen, stelt u identieke PHP-instellingen in voor zowel de PHP opdrachtregel als de PHP webserver plug-in.

Zie voor meer informatie over PHP-instellingen [Vereiste PHP-instellingen](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) in onze ontwikkelaarsdocumentatie.

### Oplossing voor uitsnijden met fouten {#solution-cron-running-with-errors}

Probeer elke opdracht handmatig uit te voeren, omdat de opdracht nuttige foutberichten kan weergeven. Zie [Uitsnijdtaken instellen](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron).

>[!NOTE]
>
>U moet minstens uitsnede uitvoeren *tweemaal* voor de uit te voeren taak; de eerste keer dat taken in de wachtrij worden geplaatst, de tweede keer dat de taken worden uitgevoerd.
