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

Dit artikel geeft de mogelijke oplossingen voor de Commerce Admin login kwestie, waar u terug naar het login formulier met het volgende foutenmelding wordt gericht: *&quot;Uw huidige zitting is verlopen&quot;*. Tot de oplossingen behoren het controleren op problemen met de instelling van de servertijd en het wijzigen van de opslaginstellingen voor sessies.

## Betrokken versies en versies:

Alle Adobe Commerce-versies en -versies

## Probleem

<u> Stappen om </u> te reproduceren:

1. Ga naar de pagina Commerce Admin.
1. Voer uw referenties in en klik op Aanmelden.

<u> Verwacht resultaat </u>:

U wordt aangemeld bij de Commerce Admin.

<u> Werkelijk resultaat </u>:

U wordt opnieuw gericht terug naar het login formulier, met het volgende getoonde foutenmelding: *&quot;Uw huidige zitting is verlopen&quot;*.

## Oorzaak

Er zijn twee mogelijke redenen voor deze kwestie:

* een probleem met de tijdinstellingen van de server
* een probleem met sessieopslag

Raadpleeg de volgende sectie voor oplossingen.

## Oplossing

### Controleren op problemen met servertijd

Controleer de sessierecord die in de tabel `admin_user_session` is gemaakt. Als de waarden van `created_at` en/of `updated_at` onjuist zijn, kan dit worden veroorzaakt door het probleem met de instellingen voor de servertijd. Vraag de systeembeheerder van het serversysteem om dat te controleren. Merk op, dat de tijd in OB aan UTC door gebrek wordt geplaatst.

### De sessieopslag wijzigen

Wijzig de sessieopslag. Gebruik info van [ hoe te om van uw zittingsdossiers ](https://devdocs.magento.com/guides/v2.3/config-guide/sessions.html) artikel in onze ontwikkelaarsdocumentatie de plaats te bepalen om te weten te komen waar uw zitting wordt opgeslagen, en het te veranderen door het `app/etc/env.php` dossier uit te geven.

Als u bijvoorbeeld een sessie wilt opslaan in het bestandssysteem, wijzigt u de sectie `'session'` als volgt:

```php
....
'session' =>
    array (
      'save' => 'files',
),
....
```

Voer de opdracht `bin/magento app:config:import` uit om configuratiegegevens te importeren.


## Gerelateerde lezing

* [ de Gegevens van de Invoer van configuratiedossiers ](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-config-mgmt-import.html) in onze ontwikkelaarsdocumentatie
* [ vorm Redis ](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html) in onze ontwikkelaarsdocumentatie
* [ Redirect terug naar de login van Commerce Admin vorm met &quot;Uw rekening is tijdelijk gehandicapt&quot;fout ](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) in onze basis van de steunkennis
* [ richt terug naar de login vorm zonder fout, wanneer het proberen om aan Commerce te login Admin ](/help/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin.md) in onze basis van de steunkennis
