---
title: 404 niet gevonden fout bij het openen van de wizard Web Setup via het deelvenster Beheer
description: Dit artikel verstrekt een oplossing voor wanneer u 404 gevonden niet fout wanneer het proberen om tot de Tovenaar van de Opstelling van het Web via het admin paneel toegang te hebben ervaart.
exl-id: 1b89da58-c872-481b-b2a0-aa48db8223db
feature: Admin Workspace, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# 404 niet gevonden fout bij het openen van de wizard Web Setup via het deelvenster Beheer

Dit artikel verstrekt een oplossing voor wanneer u 404 gevonden niet fout wanneer het proberen om tot de Tovenaar van de Opstelling van het Web via het admin paneel toegang te hebben ervaart.

## Betrokken producten en versies

* De functionaliteit van de Tovenaar van de Opstelling van het Web werd afgekeurd in Adobe Commerce (alle plaatsingsmethodes) 2.3.6 en in 2.4.0 verwijderd.

## Probleem

Wanneer het installeren van een uitbreiding die de Tovenaar van de Opstelling van het Web gebruiken toont een 404 pagina.

<u> Stappen om </u> te reproduceren:

Merchant klikt de Tovenaar van de Opstelling van het Web om nieuwe module/integratie te installeren.

<u> Verwacht resultaat </u>:

Installatie van modules/integratie.

<u> Werkelijk resultaat </u>:

Er wordt een fout van 404 weergegeven.

## Oorzaak

De wizard Web Setup is voor alle Adobe Commerce uitgeschakeld op instanties van de cloud-infrastructuur. Het is niet mogelijk deze wizard in te schakelen. Extensies moeten via een composer worden geïnstalleerd.

## Oplossing

Deze functie is uitgeschakeld in Adobe Commerce op cloudinfrastructuur.

Zie [&#x200B; installeren, beheren, en verbetert uitbreidingen &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure-store/extensions) in onze ontwikkelaarsdocumentatie voor informatie over hoe te om updates uit te voeren of externe modules voor Adobe Commerce op onze wolkeninfrastructuur te installeren.
Zie [&#x200B; Snel begin installeert &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/composer) in onze ontwikkelaarsdocumentatie voor informatie over hoe te om updates uit te voeren of externe modules voor Adobe Commerce op-gebouw te installeren.

## Gerelateerde lezing

* Zie [&#x200B; een uitbreiding &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure-store/extensions#install-an-extension) in onze ontwikkelaarsdocumentatie installeren.
