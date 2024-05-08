---
title: WAF-aanvragen voor GraphQL omzeilen
description: In dit artikel wordt uitgelegd hoe u WAF-aanvragen voor GraphQL kunt omzeilen.
feature: GraphQL
source-git-commit: c35d4ba82fbe1657756e160a73fd575c736b4e1c
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# WAF-aanvragen voor GraphQL omzeilen

In dit artikel wordt uitgelegd hoe u WAF-aanvragen voor GraphQL kunt omzeilen wanneer de [!DNL Fastly] WAF blokkeert je GraphQL-aanvragen.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur (alle versies)

## Oorzaak

Vanwege de inherente aard van GraphQL-verzoeken kunnen er veel herhaalde tekens zijn die kunnen leiden tot een fout-positieve blokkering van de aanvragen van de [!DNL Fastly] WAF.

## Oplossing

1. U kunt WAF voor deze aanvragen omzeilen door een aangepast fragment toe te voegen via het dialoogvenster [!DNL Fastly] Module Magento:

   type: recv-prioriteit: 15 inhoud:

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. Klikken op **[!UICONTROL Upload VCL to Fastly]**.

## Gerelateerde lezing

* [Web Application Firewall (WAF)](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) in Commerce on Cloud Infrastructure guide.
* [Aan de slag met aangepaste VCL](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) in Commerce on Cloud Infrastructure guide.

