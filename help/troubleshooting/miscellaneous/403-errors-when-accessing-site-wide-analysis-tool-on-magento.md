---
title: 403 fouten bij de toegang tot Site-brede Analyse Tool op Adobe Commerce
description: Dit artikel biedt een oplossing voor het gebruik van 403 fouten bij het openen van de analysefunctie voor de hele site op Adobe Commerce.
exl-id: f24fad17-62d6-4a0f-bcba-983c3dbee3d7
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# 403 fouten bij de toegang tot Site-brede Analyse Tool op Adobe Commerce

Dit artikel biedt een oplossing voor het gebruik van 403 fouten bij het openen van de analysefunctie voor de hele site op Adobe Commerce.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur 2.4.1 en hoger.

## Probleem

U krijgt een fout 403 wanneer het proberen om tot het hulpmiddel van de Analyse van de Plaats-brede toegang te hebben.

<u> Stappen om te reproduceren:</u>

Login aan het paneel van Admin van Commerce en klik **Rapporten** > *de Inzichten van het Systeem* > **Plaats-brede Hulpmiddel van de Analyse**.

<u> Verwacht resultaat:</u>

U ziet het hulpmiddel van de Analyse voor de hele site.

<u> Ware resultaat:</u>

U ziet: *Fout 403.*


## Oplossing

Om ervoor te zorgen dat het hulpmiddel van de Analyse van de Plaats-brede de juiste toegang tot uw toepassing heeft, stel het volgende bevel in CLI in werking. Vervang `<store URL>` door de URL van uw winkel:

```cURL
curl -sIL -X GET <store URL>/swat/key/index | grep HTTP
HTTP/2 403
```

Neem stappen afhankelijk van de antwoordcode u krijgt.

### 403 Verboden antwoordcode

Als de responscode 403 is, hebt u mogelijk de bescherming van de Cloudflare-bot, die het hulpprogramma voor analyse van de hele site blokkeert. Om tot het hulpmiddel toegang te hebben, whitelist zijn IP&#39;s:

* 107 23 33 174
* 3 225 9 244
* 3 88 83 85

### 200-responscode en JSON-uitvoer corrigeren

Als de reactie de correcte 200 code en output JSON is, [ voorlegt een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om de kwestie met de toegang van het Hulpmiddel van de Analyse te escaleren plaats-brede.


### Responscode van 500 (Fatale fout)

Als een responscode 500 is (Fatale fout), installeert u de MDVA-38526-patch. Gebruik een van de volgende koppelingen om de patch te downloaden, afhankelijk van het gewenste type patch:

* Adobe Commerce op het flard van de wolkeninfrastructuur: [ MDVA-38526_EE_2.4.1-p1_v3.patch.zip ](assets/MDVA-38526_EE_2.4.1-p1_v3.patch.zip)
* Adobe Commerce op de componentenflard van de wolkeninfrastructuur: [ MDVA-38526_EE_2.4.1-p1_COMPOSER_v3.patch.zip ](assets/MDVA-38526_EE_2.4.1-p1_COMPOSER_v3.patch.zip)

De patch is van toepassing op Adobe Commerce op cloudinfrastructuur versie 2.4.1 en hoger.

### Response not JSON

Als de responsuitvoer niet JSON is, kan dit te wijten zijn aan PWA/Headless-implementatie. Als u de implementatie zonder kop gebruikt, werkt u de UPWARD-configuratie bij om aanvragen naar Adobe Commerce Origin te omzeilen. Om dit, in Adobe Commerce te doen Admin, onder **Slaat** > **Configuratie** > **Algemeen** > **Web** > **de Configuratie van de PWA van de UPWARD** > **Lijst van gewenste personen van de Voornaam 11}, voeg *wat* toe.**

![ Upward_configuration ](assets/upward_pwa.png)

Als u nog niet tot het Plaats-brede Hulpmiddel van de Analyse kunt toegang hebben, wanneer u binnen aan het paneel van Commerce Admin binnen registreert en aan **Rapporten** > *de Inzichten van het Systeem* > **Plaats-brede Hulpmiddel van de Analyse** navigeert, [ voorlegt een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Gerelateerde lezing

* ](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html) de gids van het Hulpmiddel van de Analyse van 0} plaats-brede[
