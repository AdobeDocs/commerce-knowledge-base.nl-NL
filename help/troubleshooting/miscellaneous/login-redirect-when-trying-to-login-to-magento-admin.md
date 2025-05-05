---
title: Meld u opnieuw aan bij Commerce Admin om u aan te melden
description: Dit artikel bevat de mogelijke oplossingen voor het aanmeldingsprobleem van Commerce Admin, waarbij u weer naar het aanmeldingsformulier wordt omgeleid wanneer u zich probeert aan te melden bij de beheerder en er geen foutbericht wordt weergegeven. Dit zijn onder andere het corrigeren van de instellingen voor de tijdzone van de server en het wissen van de cookies-instellingen in Adobe Commerce.
exl-id: ff3114fd-8690-4983-8221-cf807f083b15
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Meld u opnieuw aan bij Commerce Admin om u aan te melden

Dit artikel bevat de mogelijke oplossingen voor het aanmeldingsprobleem van Commerce Admin, waarbij u weer naar het aanmeldingsformulier wordt omgeleid wanneer u zich probeert aan te melden bij de beheerder en er geen foutbericht wordt weergegeven. Dit zijn onder andere het corrigeren van de instellingen voor de tijdzone van de server en het wissen van de cookies-instellingen in Adobe Commerce.

## Betrokken versies en versies:

Alle Adobe Commerce-versies en -versies.

## Probleem

<u> Stappen om </u> te reproduceren:

1. Ga naar de pagina Commerce Admin.
1. Voer uw referenties in en klik op Aanmelden.

<u> Verwachte resultaten </u>:

U wordt aangemeld bij de Commerce Admin.

<u> Ware resultaten </u>:

U wordt opnieuw omgeleid naar het aanmeldingsformulier zonder foutberichten.

## Oorzaak

Er zijn een paar mogelijke redenen voor deze kwestie:

* Onjuiste tijdzone ingesteld op browserniveau (waardoor de beheersessie als verlopen wordt beschouwd, zelfs als de werkelijke levensduur nog niet is verlopen).
* Onjuiste cookies, waardoor de ingestelde sessie niet door Adobe Commerce wordt gebruikt.

Zie de volgende alinea&#39;s voor oplossingen in elk geval.

## Oplossingen

### Aanbieding tijdens beheersessie

Probeer een andere browser te gebruiken en verhoog de levensduur van de beheersessie als deze minder dan een uur bedraagt.

Voer de volgende stappen uit om de levensduur van de beheersessie te verhogen:

1. Maak een back-up van de database.
1. Gebruik een gegevensbestandhulpmiddel zoals [ phpMyAdmin ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin), of toegang manueel OB van de bevellijn om de volgende SQL vraag in werking te stellen:

   ```sql
   UPDATE core_config_data SET value = 7200 WHERE path = 'admin/security/session_lifetime';
   ```

1. Reinig het configuratiecache door het volgende bevel in werking te stellen:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

### Onjuiste cookies

Voer de volgende stappen uit om de waarden van de cookies-instellingen te controleren en te wissen:

1. Maak een back-up van de database.
1. Gebruik een gegevensbestandhulpmiddel zoals [ phpMyAdmin ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin), of toegang manueel OB van de bevellijn om de volgende SQL vraag in werking te stellen:

   ```sql
   SELECT * FROM core_config_data WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. Als de reacties van de waarden niet leeg zijn, stelt u deze in op NULL door uit te voeren:

   ```sql
   UPDATE core_config_data SET value = NULL WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. Reinig het configuratiecache door het volgende bevel in werking te stellen:

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

## Verwante artikelen

* [ richt terug naar de Admin login vorm met &quot;Uw rekening is tijdelijk gehandicapt&quot;fout ](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) in onze basis van de steunkennis.
* [ richt terug naar de Admin login vorm met &quot;Uw huidige zitting is verlopen&quot;fout ](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-current-session-has-been-expired-error.md) in onze basis van de steunkennis.
