---
title: Magento Order Management System (OMS) for Adobe Commerce times out
description: Dit artikel verstrekt een oplossing voor de kwestie waar het Systeem van het Magento Order Management (OMS) voor Adobe Commerce niet de plaatselijk geïnstalleerde micro-dienst met MOM kan registreren gebruikend inboei, omdat MOM tijden uit wanneer het proberen om terug te roepen.
exl-id: 19149d8c-ea24-46fb-8815-9f637afe46ca
feature: System
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Magento Order Management System (OMS) for Adobe Commerce times out

Dit artikel verstrekt een oplossing voor de kwestie waar het Systeem van het Magento Order Management (OMS) voor Adobe Commerce niet de plaatselijk geïnstalleerde micro-dienst met MOM kan registreren gebruikend inboei, omdat MOM tijden uit wanneer het proberen om terug te roepen.

## Betrokken producten en versies

* Adobe Commerce 2.3.1
* OMS
* ngrot

>[!WARNING]
>
>Disclaimer: Adobe Commerce beveelt geen specifiek instrument aan of bekrachtigt geen specifiek instrument voor het aanleggen van tunnels. Het voorgaande is alleen suggesties. Voor meer informatie raadpleegt u de [ngrok-documentatie](https://ngrok.com/docs).

## Probleem

<u>Stappen om te reproduceren</u>

1. Installeer Adobe Commerce in uw lokale omgeving.
1. Stel een naam in om een tunnel te maken om uw lokale server toegankelijk te maken.
1. Proberen [verbinding maken met OMS](https://omsdocs.magento.com/en/integration/connector/setup-tutorial/).

<u>Verwacht resultaat</u>

Verbinding tot stand gebracht.

<u>Werkelijk resultaat</u>

MCOM lijkt een time-out op te geven wanneer wordt geprobeerd terug te bellen naar de URL van het knooppunt.

## Oorzaak

Een van de mogelijke redenen voor de time-out is dat servers zich te ver van de locatie bevinden en dat de verbinding te veel tijd in beslag neemt.

## Oplossing

Voeg een parameter toe die het gebied aangeeft wanneer u het notitieankerpunt start. Als het volgende:

```bash
./ngrok http 80 -region eu
```

Het standaardgebied is US. Zie [alle mogelijke waarden](https://ngrok.com/docs#config_region).
