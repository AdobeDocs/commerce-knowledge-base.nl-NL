---
title: Omleiden naar het aanmeldingsformulier voor Commerce Admin met de fout "Uw huidige sessie is verlopen"
description: 'Dit artikel bevat de mogelijke oplossingen voor het aanmeldingsprobleem van Commerce Admin, waarbij u met het volgende foutbericht terugkeert naar het aanmeldingsformulier: *"Uw huidige sessie is verlopen"*. Tot de oplossingen behoren het controleren op problemen met de instelling van de servertijd en het wijzigen van de opslaginstellingen voor sessies.'
exl-id: 29df2ed2-ff4a-4f1a-bdb7-1160416cda00
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Omleiden naar het aanmeldingsformulier voor Commerce Admin met de fout &quot;Uw huidige sessie is verlopen&quot;

Dit artikel bevat de mogelijke oplossingen voor het aanmeldingsprobleem van Commerce Admin, waarbij u met het volgende foutbericht terugkeert naar het aanmeldingsformulier: *&quot;Uw huidige sessie is verlopen&quot;*. Tot de oplossingen behoren het controleren op problemen met de instelling van de servertijd en het wijzigen van de opslaginstellingen voor sessies.

## Betrokken versies en versies:

Alle Adobe Commerce-versies en -versies

## Probleem

<u>Stappen om te reproduceren</u>:

1. Ga naar de pagina Commerce Admin.
1. Voer uw referenties in en klik op Aanmelden.

<u>Verwacht resultaat</u>:

U wordt aangemeld bij de Commerce Admin.

<u>Werkelijk resultaat</u>:

U wordt opnieuw omgeleid naar het aanmeldingsformulier, met het volgende foutbericht weergegeven: *&quot;Uw huidige sessie is verlopen&quot;*.

## Oorzaak

Er zijn twee mogelijke redenen voor deze kwestie:

* een probleem met de tijdinstellingen van de server
* een probleem met sessieopslag

Raadpleeg de volgende sectie voor oplossingen.

## Oplossing

### Controleren op problemen met servertijd

Controleer de sessierecord die in het dialoogvenster `admin_user_session` tabel. Als de waarden van `created_at` en/of `updated_at` onjuist zijn, kan dit worden veroorzaakt door het probleem met de instellingen voor de servertijd. Vraag de systeembeheerder van het serversysteem om dat te controleren. Merk op, dat de tijd in OB aan UTC door gebrek wordt geplaatst.

### De sessieopslag wijzigen

Wijzig de sessieopslag. De informatie uit het dialoogvenster [Uw sessiebestanden zoeken](https://devdocs.magento.com/guides/v2.3/config-guide/sessions.html) artikel in onze ontwikkelaarsdocumentatie om te weten te komen waar uw zitting wordt opgeslagen, en het te veranderen door het uit te geven `app/etc/env.php` bestand.

Als u bijvoorbeeld wilt beginnen met het opslaan van een sessie in het bestandssysteem, wijzigt u de instelling `'session'` als volgt:

```php
....
'session' =>
    array (
      'save' => 'files',
),
....
```

Voer de `bin/magento app:config:import` om configuratiegegevens te importeren.


## Gerelateerde lezing

* [Gegevens importeren uit configuratiebestanden](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-config-mgmt-import.html) in onze documentatie voor ontwikkelaars
* [Redis configureren](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html) in onze documentatie voor ontwikkelaars
* [Omleiden naar het aanmeldingsformulier voor Commerce Admin met de fout &quot;Uw account is tijdelijk uitgeschakeld&quot;](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) in onze kennisbasis voor ondersteuning
* [Omleiden naar het aanmeldingsformulier zonder fout wanneer u zich probeert aan te melden bij de Commerce Admin](/help/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin.md) in onze kennisbasis voor ondersteuning
