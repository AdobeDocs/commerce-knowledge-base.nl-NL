---
title: E-mailberichten voor Admin 2FA worden niet ontvangen
description: Dit artikel biedt oplossingen voor problemen wanneer u geen e-mail ontvangt met de instructies voor het voltooien van de installatie nadat u Two-Factor Authentication (2FA) hebt ingesteld om de toegangsbeveiliging van Admin in Adobe Commerce op cloudinfrastructuur te verbeteren.
exl-id: 7ab6b2b4-6aca-4323-a45b-2b4e52955160
feature: Admin Workspace, Communications
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# E-mailberichten voor Admin 2FA worden niet ontvangen


## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur, alle versies

## Probleem

U hebt Two-Factor Authentificatie opstelling om de toegangsveiligheid van Admin te verbeteren, maar ontvangt niet e-mail met de instructies bij de voltooiing van de opstelling.

## Oorzaak

Als u de e-mail van de Afzender niet behoorlijk hebt gevormd, of uw domein niet wit-geëtiketteerd in SendGrid is, dan zou e-mail waarschijnlijk in de omslag Spam geëindigd hebben.

## Problemen oplossen

### Stap 1: Controleer uw map Spam

1. Als het e-mailbericht niet in uw map Spam werd weergegeven, voert u deze Mysql-query uit om te controleren of de e-mailadressen zijn geconfigureerd:

   ```sql
   select * from core_config_data where path like '%trans_email%';
   ```

   * Als het om het even welke resultaten terugkeert, betekent het dat het adres van de Afzender niet is gevormd.
   * Als er een resultaat wordt geretourneerd, gaat u verder met **Stap 2**.

1. Als het e-mailbericht in uw map Spam werd weergegeven, klikt u op de koppeling in het e-mailbericht. Als de koppeling sindsdien is verlopen, probeert u zich opnieuw aan te melden om het proces te herhalen.
1. Wanneer u toegang hebt gekregen, gaat u naar **Winkels** > **Configuratie** > **Algemeen** > **E-mailadressen van winkel** en configureer de e-mailadressen.

### Stap 2: Als/zodra de e-mailadressen behoorlijk zijn gevormd, SSH in het milieu en stel dit bevel in werking:

```php
php -r "mail(<your email address>,<subject>,<content>,'To: <sender email>');"
```

Controleer de map Spam voor de e-mail. Als de e-mail daar verscheen, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#login) om aan te vragen dat het domein wit-geëtiketteerd in SendGrid is.

## Gerelateerde lezing

* [SendGrid](https://devdocs.magento.com/cloud/project/sendgrid.html) in onze ontwikkelaarsdocumentatie.
