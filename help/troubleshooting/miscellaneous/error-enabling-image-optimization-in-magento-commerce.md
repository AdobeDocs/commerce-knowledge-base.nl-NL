---
title: Fout bij optimaliseren van afbeelding in Adobe Commerce
description: Dit artikel biedt een oplossing voor het probleem wanneer Fastly Image Optimization (IO) standaard is uitgeschakeld met een melding om snel contact op te nemen om optimalisatie van afbeeldingen in te schakelen. (De Fastly Cloud Image Optimizer is een realtime service voor het bewerken en optimaliseren van afbeeldingen die de levering van afbeeldingen versnelt door het leveren van bandbreedteefficiënte afbeeldingen.)
exl-id: 7b64c786-3c74-4642-b0d0-15b5648163a0
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Fout bij optimaliseren van afbeelding in Adobe Commerce

Dit artikel biedt een oplossing voor het probleem wanneer Fastly Image Optimization (IO) standaard is uitgeschakeld met een melding om snel contact op te nemen om optimalisatie van afbeeldingen in te schakelen. (De Fastly Cloud Image Optimizer is een realtime service voor het bewerken en optimaliseren van afbeeldingen die de levering van afbeeldingen versnelt door het leveren van bandbreedteefficiënte afbeeldingen.)

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur 2.2.x, 2.3.x

## Probleem

Op de pagina van de Snelle Configuratie, naast het Fastly IO Fragment, ziet u de Huidige staat: \_disabled \_met het volgende bericht onder: Gelieve te contacteren uw verkoopvertegenwoordiger of een e-mail te verzenden naar `support@fastly.com` om activering van optimalisatie van afbeeldingen voor uw snelservice aan te vragen.

## Oorzaak

Mogelijk is de site nog niet live. Er zijn processen om de site vooraf te laden wanneer deze live gaat in de Fastly-database.

## Oplossing

Een [Ondersteuningsticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) en vragen om optimalisatie van de afbeelding.
