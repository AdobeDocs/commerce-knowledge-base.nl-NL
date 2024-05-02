---
title: '[!DNL SendGrid] bestandsbeperking voor Adobe Commerce Cloud'
description: Dit artikel biedt een tijdelijke oplossing voor het  [!DNL SendGrid] beperking voor Adobe Commerce op cloudinfrastructuur.
feature: Deploy, Marketing Tools
role: Developer, Admin
exl-id: 48629f48-8100-4128-9211-53d947aecd49
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# [!DNL SendGrid] beperking voor Adobe Commerce Cloud

Dit artikel bevat enkele tijdelijke oplossingen voor de [!DNL SendGrid] beperking voor Adobe Commerce op Cloud-infrastructuur.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, [alle ondersteunde versies](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)


## Probleem

U probeert grote bijlagen te verzenden in e-mailberichten en deze logfouten ziet u:

In `/var/log/mail.log`

```shell
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[21408]: fatal: no-reply@xxxxxxxx.com(8080): message file too big
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[26434]: fatal: no-reply@xxxxxxxxx.com(8080): message file too big
```

In `/var/log/exception.log`

Productie:

`/app/<project-id>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Staging:

`/app/<project-id_stg>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Staging2:

`/app/<project-id_stg2>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

## Oorzaak

[!DNL SendGrid] heeft een systeembeperking van 30 MB voor e-mail. Het wordt aanbevolen geen bijlagen van meer dan 10 MB te gebruiken. Zie [Bijlagen verzenden](https://docs.sendgrid.com/ui/sending-email/attachments-with-digioh) in SendGrid-documentatie voor meer informatie.

## Workaround

* Gebruik geen bijlagen die groter zijn dan 6Mb of 10Mb.
* Overweeg het gebruik van een externe SMTP-server op uw Adobe Commerce-instantie. Raadpleeg voor stappen [E-mailcommunicatie configureren](https://experienceleague.adobe.com/docs/commerce-admin/systems/communications/email-communications.html) in onze Admin Systems Guide.
* Configureer de server opnieuw zodat bestanden in uw module kunnen worden opgeslagen en koppel de koppeling vervolgens aan de bestanden in de e-mails.

## Gerelateerde lezing

* [[!DNL SendGrid] e-mailservice](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html) in onze Commerce on Cloud Infrastructure Guide.
