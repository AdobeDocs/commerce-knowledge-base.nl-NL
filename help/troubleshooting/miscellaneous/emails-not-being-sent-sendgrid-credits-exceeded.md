---
title: E-mails niet verzonden wanneer SendGrid-credits op Adobe Commerce worden overschreden
description: Dit artikel biedt een oplossing als je e-mailberichten niet worden verzonden omdat je de limiet voor SendGrid-credits voor Adobe Commerce hebt overschreden.
exl-id: 43438890-665b-4408-8034-e61de8fbbd8b
feature: Communications, Orders
role: Developer
source-git-commit: e04bb0b37e795cae3380e1110e6db95be12036b0
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# E-mails niet verzonden wanneer SendGrid-credits op Adobe Commerce worden overschreden

## Betrokken producten en versies

* Adobe Commerce over cloudinfrastructuur 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.3

## Probleem

De credits van SendGrid verwijzen naar het aantal toegestane e-mails die kunnen worden verzonden. Er kunnen per maand slechts 12.000 e-mails worden verzonden vanuit de vertakkingen voor integratie en afbouw. Credits worden vernieuwd aan het begin van de maand, dus als er onvoldoende kredieten beschikbaar zijn, moet u wachten op de verlenging.

Het aantal e-mails dat in Productie kan worden verzonden, is onbeperkt, zolang de afzenderservice meer dan 95% bedraagt. De reputatie wordt beïnvloed door het aantal gebrande/verworpen e-mails en of op DNS-Gebaseerde spamregisters uw domein als potentiële spambron hebben gemarkeerd. In Productie worden in totaal 12.000 e-mails per dag toegewezen, maar dat aantal kan worden uitgebreid op basis van het gemiddelde aantal e-mails dat in de afgelopen vijf dagen is verzonden.

## Hoe kan ik controleren of je crediteringen zijn overschreden?

Adobe Commerce on cloud Infrastructure Pro-planarchitectuur: controleer de `/var/log/mail.log` - u zou een bericht als dit kunnen zien:

`May 28 21:13:00 <i-node> postfix/error[21335]: BC7941A2BBF: to=<to@email.com>, relay=none, delay=4642, delays=4642/0.56/0/0.03, dsn=4.0.0, status=deferred (delivery temporarily suspended: SASL authentication failed; server smtp.sendgrid.net[ip address] said: 451 Authentication failed: Maximum credits exceeded).`

## Oorzaak

Het aantal toegestane e-mailberichten dat kan worden verzonden, is beperkt.

## Oplossing

* Als dit bericht wordt weergegeven in de productieomgeving, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) en verstrek het bovenstaande bericht en verzoek om een verhoging van de kredieten.
* Als dit bericht niet wordt weergegeven of als u zich op Adobe Commerce bevindt op de Starter-planarchitectuur van de cloud [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) en vermelden dat de `mail.log` geeft niet aan dat de credits zijn overschreden.

## Gerelateerde lezing

* [SendGrid](https://devdocs.magento.com/cloud/project/sendgrid.html) in onze ontwikkelaarsdocumentatie.
