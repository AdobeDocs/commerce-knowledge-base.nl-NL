---
title: 'Adobe Commerce cloud: opnieuw indexeren wordt afgesloten met een ''Killed''-bericht'
description: '* Adobe Commerce op cloudinfrastructuur (alle versies)'
exl-id: 36ed9c9f-8280-41db-9df3-fe842dade4b1
feature: Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Adobe Commerce-cloud: opnieuw indexeren wordt beëindigd met `Killed` -bericht

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur (alle versies)

## Probleem

U probeert om een herdex op de tak van de Integratie (of bij het Opvoeren van het de architectuurproject van de Aanzet) in werking te stellen, en het proces wordt geëindigd met het `Killed` bericht.

## Oorzaak

Dit gebeurt meestal omdat er onvoldoende geheugen beschikbaar is voor PHP-processen.
De meest algemene reden hiervoor is bijvoorbeeld een groot aantal producten, winkels en/of klantengroepen.

## Oplossing

1. Verminder het aantal producten (en klantgroepen en winkels, indien van toepassing).
1. Gebruik beperken tot een of twee gelijktijdige gebruikers.
1. Schakel de taken voor uitsnijden uit en voer indien nodig handmatig uit.
1. Als dit niet eerder is gedaan, verzoek om een verbetering aan de Verbeterde milieu&#39;s van de Integratie - neem nota van de beperking op het aantal milieu&#39;s u tot beperkt zou zijn zodra de verbetering is uitgevoerd. Verwijs naar het [ verzoek van de Verbetering van het Milieu van de Integratie - Pro en 1} artikel van de Aanzet in onze basis van steunkennis voor details.](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md)

## Gerelateerde lezing:

In onze documentatie voor ontwikkelaars:

* [ Pro architectuur > het milieu van de Integratie ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [ de architectuur van de Aanzet > het Opvoeren milieu ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#cloud-arch-stage)
