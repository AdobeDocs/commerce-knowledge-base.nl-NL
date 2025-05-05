---
title: Verliesde "oauth_tokens"verminderen vóór 2.4.6 verbetering
description: Dit artikel verstrekt een oplossing voor de kwestie waar u een groot aantal &grave; oauth_tokens &grave; in uw lijst &grave; oauth_token &grave; ziet, die een lange vertraging in verbetering tot versie 2.4.6 kan veroorzaken. Het wordt aanbevolen de tabel &grave; oauth_token&grave; te verkleinen met CleanExpiredTokens.php.
feature: Variables, Upgrade
role: Developer
exl-id: 92d1d15a-04da-4ba4-b6b8-5c491af9c4c1
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Verlagen van verlopen `oauth_tokens` vóór upgrade van 2.4.6

Dit artikel biedt een oplossing voor het probleem waarbij een groot aantal `oauth_tokens` in uw `oauth_token` -tabel wordt weergegeven. Hierdoor kan de upgrade naar versie 2.4.6 veel langer duren. Het wordt aanbevolen de tabel `oauth_token` te verkleinen met de taak [`CleanExpiredTokens.php` ](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] om de verlopen tokens te verwijderen.

## Betrokken producten en versies

* Adobe Commerce 2.4.0 - 2.4.6, alle plaatsingsmethodes

## Probleem

Als er een groot aantal `oauth_tokens` in uw `oauth_token` -tabel staat, kan dit een lange vertraging veroorzaken bij het upgraden naar versie 2.4.6.

Het verbeteringsproces omvat het coderen van die tokens voor een extra laag van veiligheid, en het is slechts 100 verslagen tegelijkertijd gedaan. Dit kan enkele uren duren als er een groot aantal tokens is.

Als u een groot aantal `oauth_tokens` in uw `oauth_token` -tabel reduceert, voorkomt u een lange vertraging bij het upgraden naar versie 2.4.6.

## Oplossing

Voordat u een upgrade start, moet u eerst controleren of de [`CleanExpiredTokens.php` ](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] -taak wordt uitgevoerd. Hierdoor wordt de tabel `oauth_token` kleiner door de verlopen `oauth_tokens` -tokens te verwijderen. Deze moeten al standaard zijn ingeschakeld.

Voer de volgende handelingen uit om de [`CleanExpiredTokens.php` ](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] -taak handmatig te activeren:
```bin/magento cron:run --group=default```

## Gerelateerde lezing

* [ de Diensten >  [!DNL OAuth] ](https://experienceleague.adobe.com/docs/commerce-admin/config/services/oauth.html) in de gids van de Verwijzing van de Configuratie van Commerce
* [ Gids van de Authentificatie ](https://developer.adobe.com/developer-console/docs/guides/authentication/) in de gids van Adobe Developer
* [ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
