---
title: Verliesde "oauth_tokens"verminderen vóór 2.4.6 verbetering
description: Dit artikel verstrekt een oplossing voor de kwestie waar u een groot aantal ` oauth_tokens ` in uw lijst ` oauth_token ` ziet, die een lange vertraging in verbetering tot versie 2.4.6 kan veroorzaken. Het wordt aanbevolen de tabel ` oauth_token` te verkleinen met CleanExpiredTokens.php.
feature: Variables, Upgrade
role: Developer
exl-id: 92d1d15a-04da-4ba4-b6b8-5c491af9c4c1
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Verlagen verlopen `oauth_tokens` vóór upgrade naar 2.4.6

Dit artikel biedt een oplossing voor het probleem waarbij een groot aantal `oauth_tokens` in uw `oauth_token` tabel, die een lange vertraging kan veroorzaken bij de upgrade naar versie 2.4.6. Het wordt aanbevolen de `oauth_token` tabel met de [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] taak om de verlopen tokens te verwijderen.

## Betrokken producten en versies

* Adobe Commerce 2.4.0 - 2.4.6, alle plaatsingsmethodes

## Probleem

Als er een groot aantal `oauth_tokens` in uw `oauth_token` die een lange vertraging kan veroorzaken bij de upgrade naar versie 2.4.6.

Het verbeteringsproces omvat het coderen van die tokens voor een extra laag van veiligheid, en het is slechts 100 verslagen tegelijkertijd gedaan. Dit kan enkele uren duren als er een groot aantal tokens is.

Een groot aantal `oauth_tokens` in uw `oauth_token` tabel kan een lange vertraging bij de upgrade naar versie 2.4.6 voorkomen.

## Oplossing

Voordat u een upgrade start, moet u eerst controleren of de [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] taak wordt uitgevoerd. Hierdoor wordt de grootte van de `oauth_token` tabel door de verlopen te verwijderen `oauth_tokens` tokens, en zou reeds door gebrek moeten worden toegelaten.

Als u de [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] taak, uitvoeren:
```bin/magento cron:run --group=default```

## Gerelateerde lezing

* [Services > [!DNL OAuth]](https://experienceleague.adobe.com/docs/commerce-admin/config/services/oauth.html) in de handleiding Commerce Configuration Reference.
* [Verificatiehandleiding](https://developer.adobe.com/developer-console/docs/guides/authentication/) in de handleiding van Adobe Developer.
