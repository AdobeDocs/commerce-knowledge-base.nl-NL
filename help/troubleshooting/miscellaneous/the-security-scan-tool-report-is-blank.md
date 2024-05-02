---
title: Het rapport Beveiligingsscan Tool is leeg
description: Dit artikel bevat een oplossing voor het probleem waarbij met het gereedschap Beveiligingsscan een lege pagina wordt weergegeven in plaats van het werkelijke rapport. Om het op te lossen, zou u IPs kunnen moeten toevoegen die door het Hulpmiddel aan de firewallLijst van gewenste personen wordt gebruikt.
exl-id: e5f7f8c6-2dd3-44e3-8d19-f1f38d06dd6c
feature: Compliance, Security
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Het rapport Beveiligingsscan Tool is leeg

Dit artikel bevat een oplossing voor het probleem waarbij met het gereedschap Beveiligingsscan een lege pagina wordt weergegeven in plaats van het werkelijke rapport. Om het op te lossen, zou u IPs kunnen moeten toevoegen die door het Hulpmiddel aan de firewallLijst van gewenste personen wordt gebruikt.

## Betrokken producten en versies:

* Adobe Commerce (alle implementatiemethoden) en Magento Open Source, alle versies

## Probleem

<u>Stappen om te reproduceren</u>:

1. Configureer het hulpprogramma Beveiligingsscan om uw website te controleren, zoals beschreven in [Beveiligingsscan](https://docs.magento.com/m2/ee/user_guide/magento/security-scan.html) in onze gebruikershandleiding.
1. Selecteer in de kolom Handelingen de optie **Scan uitvoeren**.

<u>Verwachte resultaten</u>:

Bekijk het bericht van de rapportvoltooiing en de capaciteit om het rapport te openen.

<u>Werkelijke resultaten</u>:

Geen melding en geen rapport beschikbaar.

## Oorzaak

Dit probleem kan optreden omdat het hulpprogramma voor beveiligingsscan uw website niet kan bereiken. Dit betekent dat de website niet bereikbaar is of dat het hulpprogramma voor beveiligingsscan wordt geblokkeerd.

## Oplossing

Probeer uw website te openen.

* Als de pagina met succes wordt geladen, zou u IPs kunnen moeten toevoegen die door de Hulpmiddelen van het Scannen van de Veiligheid aan de Lijst van gewenste personen van de firewall wordt gebruikt. De volgende IP&#39;s worden gebruikt: 52.87.98.44, 34.196.167.176, 3.218.25.102 in de havens 80 en 443.
* Als de site het bestand niet laadt en retourneert *&quot;Er is een fout opgetreden bij het verwerken van uw verzoek.&quot;* bericht, controleer uw website op mogelijke fouten.

## Gerelateerde lezing

* [Live gaan en starten](https://devdocs.magento.com/guides/v2.3/cloud/live/live.html?_ga=2.73579601.273749082.1559572284-888339099.1547722854#security-scan) in onze ontwikkelaarsdocumentatie.
* [Beveiligingsscan](https://docs.magento.com/m2/ee/user_guide/magento/security-scan.html) in onze gebruikershandleiding.
