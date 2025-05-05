---
title: Het rapport Beveiligingsscan Tool is leeg
description: Dit artikel bevat een oplossing voor het probleem waarbij met het gereedschap Beveiligingsscan een lege pagina wordt weergegeven in plaats van het werkelijke rapport. Om het op te lossen, zou u IPs kunnen moeten toevoegen die door het Hulpmiddel aan de firewallLijst van gewenste personen wordt gebruikt.
exl-id: e5f7f8c6-2dd3-44e3-8d19-f1f38d06dd6c
feature: Compliance, Security
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Het rapport Beveiligingsscan Tool is leeg

Dit artikel bevat een oplossing voor het probleem waarbij met het gereedschap Beveiligingsscan een lege pagina wordt weergegeven in plaats van het werkelijke rapport. Om het op te lossen, zou u IPs kunnen moeten toevoegen die door het Hulpmiddel aan de firewallLijst van gewenste personen wordt gebruikt.

## Betrokken producten en versies:

* Adobe Commerce (alle implementatiemethoden) en Magento Open Source, alle versies

## Probleem

<u> Stappen om </u> te reproduceren:

1. Vorm het Hulpmiddel van het Scannen van de Veiligheid om uw website te controleren, zoals die in [ Scannen van de Veiligheid ](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/security/security-scan) in onze gebruikersgids wordt beschreven.
1. In de kolom van Acties, uitgezochte **Scannen van de Looppas**.

<u> Verwachte resultaten </u>:

Bekijk het bericht van de rapportvoltooiing en de capaciteit om het rapport te openen.

<u> Ware resultaten </u>:

Geen melding en geen rapport beschikbaar.

## Oorzaak

Dit probleem kan optreden omdat het hulpprogramma voor beveiligingsscan uw website niet kan bereiken. Dit betekent dat de website niet bereikbaar is of dat het hulpprogramma voor beveiligingsscan wordt geblokkeerd.

## Oplossing

Probeer uw website te openen.

* Als de pagina met succes wordt geladen, zou u IPs kunnen moeten toevoegen die door de Hulpmiddelen van het Scannen van de Veiligheid aan de Lijst van gewenste personen van de firewall wordt gebruikt. De volgende IP&#39;s worden gebruikt: 52.87.98.44, 34.196.167.176, 3.218.25.102 in de havens 80 en 443.
* Als de plaats niet laadt en *&quot;Er is een fout geweest die uw verzoek&quot;verwerkt* bericht, uw website voor mogelijke fouten controleert.

## Gerelateerde lezing

* [ ga levend en lanceer ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/launch/overview) in onze ontwikkelaardocumentatie.
* [ Scannen van de Veiligheid ](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/security/security-scan) in onze gebruikersgids.
