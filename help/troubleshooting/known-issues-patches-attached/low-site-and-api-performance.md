---
title: Lage site- en API-prestaties
description: Dit artikel biedt een patch voor het bekende Adobe Commerce-probleem met cloudinfrastructuur 2.2.1 dat te maken heeft met een lage site- en API-prestaties die worden veroorzaakt door een lange tijd die nodig is om 'debug.log' te schrijven.
exl-id: b71816cd-f580-4c80-9694-585ed051a56d
feature: REST, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Lage site- en API-prestaties

Dit artikel biedt een patch voor het bekende Adobe Commerce-probleem met cloudinfrastructuur 2.2.1 dat te maken heeft met een lage site- en API-prestaties die worden veroorzaakt door een lange tijd die nodig is om te schrijven `debug.log`.

## Probleem

De prestaties van de site zijn traag. API-bewerkingen worden traag uitgevoerd, bijvoorbeeld wanneer u producten bijwerkt met de `PUT` methode. Wanneer u de bewerkingen met New Relic nader bekijkt, wordt het meeste geheugen en de CPU verbruikt door te schrijven naar `/var/log/debug.log`.

## Oplossing

U kunt dit probleem oplossen door de pleister aan te brengen. De patch splitst en schrijft het logbestand, de betalingsmethode en de verzendmethoden naar afzonderlijke bestanden.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[MDVA-8371\_EE\_2.2.1\_COMPOSER\_v2.patch downloaden](assets/MDVA-8371_EE_2.2.1_COMPOSER_v2.patch.zip)

### Compatibele Adobe Commerce-versies

De patch is gemaakt voor:

* Adobe Commerce over wolkeninfrastructuur 2.2.1

De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende versies en edities van de Adobe:

* Adobe Commerce over cloudinfrastructuur 2.2.0, 2.2.2, 2.2.3
* Adobe Commerce op locatie 2.2.0, 2.2.2, 2.2.3

## Hoe de pleister aanbrengen

Zie [Een door Adobe Commerce geleverde componentpatch toepassen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze kennisbasis voor ondersteuning voor instructies.

## Bijgevoegde bestanden
