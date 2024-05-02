---
title: Geavanceerde rapportage bijwerken om op een eigen uitsnijdgroep te worden uitgevoerd
description: Dit artikel biedt een patch voor het bekende probleem voor Adobe Commerce op cloudinfrastructuur 2.3.0, waarbij Advanced Reporting geen gegevens weergeeft. Dit is omdat de Geavanceerde baan van de Rapportering ` analytics_collect_data' niet volgens programma wordt uitgevoerd. Dit artikel verstrekt een flard die een Geavanceerde groep ` analytics ` zal creëren van het Overzicht.
exl-id: 8aff9e2b-d9be-4136-975b-05963e23f55c
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Geavanceerde rapportage bijwerken om op een eigen uitsnijdgroep te worden uitgevoerd

Dit artikel biedt een patch voor het bekende probleem voor Adobe Commerce op cloudinfrastructuur 2.3.0, waarbij Advanced Reporting geen gegevens weergeeft. Dit komt omdat de functie Geavanceerde rapportage `analytics_collect_data` wordt niet volgens schema uitgevoerd. Dit artikel verstrekt een flard die tot een Geavanceerde het cron van de Rapportering groep zal leiden `analytics`.

## Probleem

Er worden geen gegevens geladen in de module Geavanceerde rapportage.

## Reparatie

De patch is aan dit artikel gekoppeld. De pleister verplaatst de `analytics` taaktaken van standaardgroep samenvoegen in `analytics`.

Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[MDVA-19640\_EE\_2.3.0\_COMPOSER\_v1.patch](assets/MDVA-19640_EE_2.3.0_COMPOSER_v1.patch.zip)

Nadat u de patch hebt toegepast, voert u de volgende SQL-query uit. De query moet worden uitgevoerd om records te wijzigen in `cron_schedule` tabel.

```
UPDATE core_config_data
SET `path` = REPLACE(path, "crontab/default/jobs/analytics", "crontab/analytics/jobs/analytics")
WHERE `path` LIKE "crontab/default/jobs/analytics%";
```

### Compatibele Adobe Commerce-versies:

De patch is gemaakt voor

* Adobe Commerce over cloudinfrastructuur 2.3.0

De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -edities: 2.2.2-2.2.10, 2.3.0-2.3.2 en 2.3.2-p2 en 2.3.3, voor Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur

## Hoe de pleister aanbrengen

Zie [Hoe een door Adobe geleverde componentpleister aanbrengen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies.

## Bijgevoegde bestanden
