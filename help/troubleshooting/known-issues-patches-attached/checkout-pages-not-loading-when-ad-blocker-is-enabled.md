---
title: Pagina's die niet worden geladen uitchecken wanneer de functie voor het blokkeren van advertenties is ingeschakeld
description: Dit artikel bevat een patch voor het bekende Adobe Commerce-probleem met de cloudinfrastructuur 2.2.2 dat te maken heeft met het niet laden van uitcheckpagina's die worden veroorzaakt door blokkeerders van eBlock of andere advertenties.
exl-id: fe718f21-df23-4ab1-a6b0-03bad4d7095d
feature: Checkout, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# Pagina&#39;s die niet worden geladen uitchecken wanneer de functie voor het blokkeren van advertenties is ingeschakeld

Dit artikel bevat een patch voor het bekende Adobe Commerce-probleem met de cloudinfrastructuur 2.2.2 dat te maken heeft met het niet laden van uitcheckpagina&#39;s die worden veroorzaakt door blokkeerders van eBlock of andere advertenties.

## Probleem

Als Googles Analytics zijn ingeschakeld voor de winkel, wordt het laden van het bestand `trackingCode.js` geblokkeerd en wordt de uitvoeringsstroom van het JS onderbroken als een klant met een geïnstalleerd blokkeerprogramma of een andere advertentieblokker het uitchecken uitvoert. Dit veroorzaakt problemen met het laden van de checkout pagina.

<u> Stappen om </u> te reproduceren:

Vereisten: een advertentieblokker moet in de browser zijn geïnstalleerd en actief zijn.

1. In Commerce Admin, laat en vormt de functionaliteit van Googles Analytics toe.
1. Open een productpagina in de winkel.
1. Voeg producten toe aan de kar.
1. Klik **gaan naar Betalen** verbinding.

<u> Verwacht resultaat </u>: De paginaladingen van de Afhandeling en de klant kunnen afhandeling voltooien.

<u> Ware resultaat </u>: De pagina van de Controle laadt niet; het ladende spinner verdwijnt nooit.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[Download MDVA-9353\_EE\_2.2\_v1.composer.patch](assets/MDVA-9353_EE_2.2.2_v1.composer.patch.zip)

### Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce over wolkeninfrastructuur 2.2.2

De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce op cloudinfrastructuur van 2.1.0 tot 2.1.14
* Adobe Commerce op cloudinfrastructuur van 2.2.0 tot 2.2.1 en 2.2.3 tot 2.2.5
* Adobe Commerce op locatie van 2.1.0 tot en met 2.1.14
* Adobe Commerce op locatie van 2.2.0 tot 2.2.5

## Hoe de pleister aanbrengen

Voor instructies, zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze steunkennisbasis wordt verstrekt.

## Nuttige koppelingen

* [ de kwestie die op GitHub ](https://github.com/magento/magento2/pull/13061) wordt besproken

## Bijgevoegde bestanden
