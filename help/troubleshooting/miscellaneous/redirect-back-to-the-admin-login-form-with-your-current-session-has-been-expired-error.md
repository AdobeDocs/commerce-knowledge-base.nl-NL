---
title: Leid terug naar het [!UICONTROL Commerce Admin] aanmeldingsformulier met de fout "Uw huidige sessie is verlopen"
description: 'Dit artikel bevat de mogelijke oplossingen voor het [!UICONTROL Commerce Admin] -aanmeldingsprobleem, waarbij u met het volgende foutbericht terugkeert naar het aanmeldingsformulier: *"Uw huidige sessie is verlopen"*. Tot de oplossingen behoren het controleren op problemen met de instelling van de servertijd en het wijzigen van de opslaginstellingen voor sessies.'
exl-id: 29df2ed2-ff4a-4f1a-bdb7-1160416cda00
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Leid terug naar het [!UICONTROL Commerce Admin] aanmeldingsformulier met de fout &quot;Uw huidige sessie is verlopen&quot;

Dit artikel geeft de mogelijke oplossingen voor de [!UICONTROL Commerce Admin] login kwestie, waar u terug naar het login formulier met het volgende foutenmelding wordt gericht: *&quot;Uw huidige zitting is verlopen&quot;*. Tot de oplossingen behoren het controleren op problemen met de instelling van de servertijd en het wijzigen van de opslaginstellingen voor sessies.

## Betrokken versies en versies:

Alle Adobe Commerce-versies en -versies

## Probleem

<u> Stappen om </u> te reproduceren:

1. Ga naar de pagina **[!UICONTROL Commerce Admin]** .
1. Ga uw geloofsbrieven in en klik **binnen Teken**.

<u> Verwacht resultaat </u>:

U wordt het programma geopend aan [!UICONTROL Commerce Admin].

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

Wijzig de sessieopslag. Gebruik info van [ hoe te om van uw zittingsdossiers ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/session-storage/sessions) artikel in onze ontwikkelaarsdocumentatie de plaats te bepalen om te weten te komen waar uw zitting wordt opgeslagen, en het te veranderen door het `app/etc/env.php` dossier uit te geven.

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

* [ de Gegevens van de Invoer van configuratiedossiers ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configuration-management/import-configuration) in onze ontwikkelaarsdocumentatie
* [ vorm  [!DNL Redis] ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/redis/config-redis) in onze ontwikkelaarsdocumentatie
* [ richt terug naar de [!UICONTROL Commerce Admin] login vorm met &quot;Uw rekening is tijdelijk gehandicapt&quot;fout ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error) in onze basis van de steunkennis
* [ richt terug naar de login vorm zonder fout, wanneer het proberen om aan [!UICONTROL Commerce Admin] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin) in onze basis van de steunkennis aan te melden
* [ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce

