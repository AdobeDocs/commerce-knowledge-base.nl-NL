---
title: Problemen met gereedheid voor uitsnijden
description: '''Dit artikel biedt oplossingen voor problemen met de gereedheid voor uitsnijden. Hieronder volgen de symptomen van problemen met de kron: "'
exl-id: 1f2cee2c-98ad-4cf5-af16-d736fced2a15
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Problemen met gereedheid voor uitsnijden

Dit artikel biedt oplossingen voor problemen met gereedheid voor uitsnijden. Hieronder volgen de symptomen van problemen met de borst:

* Een foutbericht over de PHP-instelling `$HTTP_RAW_POST_DATA` wordt weergegeven, ook al is de instelling correct ingesteld.
* De PHP gereedheidscontrole geeft de PHP versie niet weer zoals de volgende afbeelding laat zien:
  ![upgr-tshoot-no-cron.png](assets/upgr-tshoot-no-cron.png)
* De volgende fout wordt weergegeven in Commerce Admin:
  ![compman-cron-not-running.png](assets/compman-cron-not-running.png)
Om de fout te zien, zou u kunnen moeten klikken **Systeemberichten** boven aan het venster als volgt:
  ![compman_sys-messages.png](assets/compman_sys-messages.png)

## De bestaande tab controleren {#check-your-existing-crontab}

In deze sectie wordt besproken hoe u kunt zien of de uitsnede momenteel wordt uitgevoerd en of deze op de juiste wijze is ingesteld.

Om te controleren of uw tab is ingesteld:

1. Meld u aan bij uw Commerce-server als of schakel over naar de [Bestandseigenaar Magento](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html).
1. Controleer of het volgende bestand bestaat: `$ ls -al <magento_root>/var/.setup_cronjob_status`. Als het bestand bestaat, is het uitsnijden in het verleden gelukt. Als het bestand *niet* bestaat, of u hebt nog niet geïnstalleerd Adobe Commerce of cron loopt niet. Ga in beide gevallen verder met de volgende stap.
1. Meer informatie over uitsnijden. Als gebruiker met `root` rechten, voert u de volgende opdracht in: `$ crontab -u <Magento file system owner name> -l`. Bijvoorbeeld op CentOS `$ crontab -u magento_user -l`. Als er geen tab voor de gebruiker is ingesteld, wordt het volgende bericht weergegeven:    `no crontab for magento_user`. Uw tab geeft het volgende weer:
   * Wat gebruikt PHP binair u (in sommige gevallen, hebt u meer dan één)
   * Welke Adobe Commerce-scripts worden uitgevoerd (in het bijzonder de paden naar die scripts)
   * Waar uw uitsnijdlogs zich bevinden

   Zie een van de volgende secties voor een oplossing van uw probleem.

## Oplossing: crontab niet ingesteld {#solution-crontab-not-set-up}

Als u wilt controleren of de uitsnijdtaken correct zijn ingesteld, raadpleegt u [Uitsnijdtaken instellen](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron) in onze ontwikkelaarsdocumentatie.

## Oplossing: uit onjuist binair PHP-bestand doorsnijden {#solution-cron-running-from-incorrect-php-binary}

Als uw uitsnijdtaak een binair PHP-bestand gebruikt dat afwijkt van de insteekmodule voor de webserver, kunnen fouten in de PHP-instellingen worden weergegeven. Om dit probleem op te lossen, stelt u identieke PHP-instellingen in voor zowel de PHP opdrachtregel als de PHP webserver plug-in.

Zie voor meer informatie over PHP-instellingen [Vereiste PHP-instellingen](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) in onze ontwikkelaarsdocumentatie.

## Oplossing: fout bij uitvoeren {#solution-cron-running-with-errors}

Probeer elke opdracht handmatig uit te voeren, omdat de opdracht nuttige foutberichten kan weergeven. Zie [Uitsnijdtaken instellen](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron) in onze ontwikkelaarsdocumentatie.

>[!NOTE]
>
>U moet minstens uitsnede uitvoeren *tweemaal* voor de uit te voeren taak; de eerste keer dat taken in de wachtrij worden geplaatst, de tweede keer dat de taken worden uitgevoerd.
