---
title: E-mailberichten voor Admin 2FA worden niet ontvangen
description: Dit artikel biedt oplossingen voor problemen wanneer u geen e-mail ontvangt met de instructies voor het voltooien van de installatie nadat u Two-Factor Authentication (2FA) hebt ingesteld om de toegangsbeveiliging van Admin in Adobe Commerce op cloudinfrastructuur te verbeteren.
exl-id: 7ab6b2b4-6aca-4323-a45b-2b4e52955160
feature: Admin Workspace, Communications
role: Developer
source-git-commit: 435a545adcf2a1d6b023abaec55c4b73e942ee1a
workflow-type: tm+mt
source-wordcount: '300'
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
Aangezien u geen toegang tot admin hebt, zult u de configuratie in het gegevensbestand moeten opnemen. Sluit het juiste e-mailadres aan en voer de MySQL-instructie uit:

   ```
   insert into core_config_data (scope,scope_id,path,value) values ('default',0,'trans_email/ident_general/email', your-email@here.com)
   ```

   * Als het een resultaat terugkeert, ga aan **Stap 2** te werk.

1. Als het e-mailbericht in uw map Spam werd weergegeven, klikt u op de koppeling in het e-mailbericht. Als de koppeling sindsdien is verlopen, probeert u zich opnieuw aan te melden om het proces te herhalen.
1. Zodra u toegang hebt gekregen, ga **>** Configuratie **>** Algemene **>** E-mailadressen van de Opslag **en vorm de e-mailadressen.**

### Stap 2: Als/zodra de e-mailadressen behoorlijk zijn gevormd, SSH in het milieu en stel dit bevel in werking:

```php
php -r "mail(<your email address>,<subject>,<content>,'To: <sender email>');"
```

Controleer de map Spam voor de e-mail. Als e-mail daar verscheen, [ voorlegt een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#login) om het domein te verzoeken om wit-geëtiketteerd in SendGrid zijn.

## Gerelateerde lezing

* [ SendGrid ](https://devdocs.magento.com/cloud/project/sendgrid.html) in onze ontwikkelaarsdocumentatie.
