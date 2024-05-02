---
title: Meld u opnieuw aan bij Commerce Admin om u aan te melden
description: Dit artikel bevat de mogelijke oplossingen voor het aanmeldingsprobleem van Commerce Admin, waarbij u weer naar het aanmeldingsformulier wordt omgeleid wanneer u zich probeert aan te melden bij de beheerder en er geen foutbericht wordt weergegeven. Dit zijn onder andere het corrigeren van de instellingen voor de tijdzone van de server en het wissen van de cookies-instellingen in Adobe Commerce.
exl-id: ff3114fd-8690-4983-8221-cf807f083b15
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Meld u opnieuw aan bij Commerce Admin om u aan te melden

Dit artikel bevat de mogelijke oplossingen voor het aanmeldingsprobleem van Commerce Admin, waarbij u weer naar het aanmeldingsformulier wordt omgeleid wanneer u zich probeert aan te melden bij de beheerder en er geen foutbericht wordt weergegeven. Dit zijn onder andere het corrigeren van de instellingen voor de tijdzone van de server en het wissen van de cookies-instellingen in Adobe Commerce.

## Betrokken versies en versies:

Alle Adobe Commerce-versies en -versies.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Ga naar de pagina Commerce Admin.
1. Voer uw referenties in en klik op Aanmelden.

<u>Verwachte resultaten</u>:

U wordt aangemeld bij de Commerce Admin.

<u>Werkelijke resultaten</u>:

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
1. Een databasegereedschap gebruiken, zoals [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin)U kunt de volgende SQL-query ook handmatig vanaf de opdrachtregel openen:

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
1. Een databasegereedschap gebruiken, zoals [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin)U kunt de volgende SQL-query ook handmatig vanaf de opdrachtregel openen:

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

* [Omleiden naar het aanmeldingsformulier voor Admin met de fout &quot;Uw account is tijdelijk uitgeschakeld&quot;](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) in onze kennisbasis voor ondersteuning.
* [Omleiden naar het aanmeldingsformulier voor Admin met de fout &quot;Uw huidige sessie is verlopen&quot;](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-current-session-has-been-expired-error.md) in onze kennisbasis voor ondersteuning.
