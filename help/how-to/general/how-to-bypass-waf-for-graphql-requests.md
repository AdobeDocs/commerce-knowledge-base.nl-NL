---
title: WAF-aanvragen voor GraphQL omzeilen
description: In dit artikel wordt uitgelegd hoe u WAF-aanvragen voor GraphQL kunt omzeilen.
feature: GraphQL
exl-id: 3a0f2c22-f976-4596-b6a9-4634be1ea4c3
source-git-commit: 2bec86818336a9ef4d8316e257a0ca4256cdd93c
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# WAF-aanvragen voor GraphQL omzeilen

In dit artikel wordt uitgelegd hoe u WAF-aanvragen voor GraphQL kunt omzeilen wanneer de [!DNL Fastly] WAF uw GraphQL-aanvragen blokkeert.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur (alle versies)

## Oorzaak

Vanwege de inherente aard van GraphQL-aanvragen kunnen er veel herhaalde tekens zijn die het blokkeren van aanvragen door de WAF-instructie van [!DNL Fastly] op valse positiefpunten kunnen activeren.

## Oplossing

1. U kunt WAF voor deze aanvragen omzeilen door een aangepast fragment toe te voegen via de module Magento [!DNL Fastly] :

   type: recv
prioriteit : 15
inhoud:

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. Klik op **[!UICONTROL Upload VCL to Fastly]** .

## Gerelateerde lezing

* [ Firewall van de Toepassing van het Web (WAF) ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) in Commerce op de gids van de Infrastructuur van de Wolk.
* [ Begonnen het worden met douane VCL ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) in Commerce op de gids van de Infrastructuur van de Wolk.
