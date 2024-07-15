---
title: Meerdere snijtaken gepland voor dezelfde periode
description: Dit artikel bevat een patch voor een bekende Adobe Commerce 2.2.2-uitgave die betrekking heeft op het feit dat meerdere snijtaken gepland zijn om tegelijk te worden uitgevoerd nadat de tijdvariabelen voor bepaalde taken in Commerce Admin zijn bewerkt.
exl-id: a3c1fe77-ed4c-43b5-8d6f-e5c549096c73
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---

# Meerdere snijtaken gepland voor dezelfde periode

Dit artikel bevat een patch voor een bekende Adobe Commerce 2.2.2-uitgave die betrekking heeft op het feit dat meerdere snijtaken gepland zijn om tegelijk te worden uitgevoerd nadat de tijdvariabelen voor bepaalde taken in Commerce Admin zijn bewerkt.

## Probleem

Wanneer het overzicht wordt gevormd om elke minuut in werking te stellen, als u tijdvariabelen voor drie geplande taken in Admin uitgeeft, toont de `cron_schedule` gegevensbestandlijst groepen veelvoudige taken die tezelfdertijd worden gepland te lopen.

<u> Stappen om </u> te reproduceren:

1. In Commerce Admin, navigeer aan **Opslag** > Montages > **Configuratie** > **GEAVANCEERD** > **Systeem** > **Gewas (Gepland Taken)** > **de configuratieopties van de Kroon voor groep: gebrek.**
1. Configureer de volgende opties:
   * **Opruiming van de Geschiedenis Elke**: ontruim het **systeem** checkbox van het Gebruik, en reeks aan *1440*.
   * **Levensduur van de Geschiedenis van het Succes**: ontruim het **systeem** checkbox van het Gebruik, en reeks aan *1440*.
   * **Levensduur van de Geschiedenis van de Mislukking**: ontruim het **systeem** checkbox van het Gebruik, en reeks aan *1440*.

1. Klik **sparen Config**.
1. Voer in SSH de opdracht `crontab -e` uit.
1. Stel de kroon in op elke minuut.
1. Open drie eindtabbladen/vensters.
1. Ga naar de map Adobe Commerce `root/base/project` in elk terminalvenster.
1. Voer de volgende opdracht uit in elk tabblad/venster:

   ```bash
   bin/magento cache:flush && bin/magento cron:run && bin/magento cache:flush && bin/magento cron:run
   ```

1. Ga naar MySQL en voer de volgende query uit:

   ```sql
   SELECT job_code, scheduled_at, count as count FROM cron_schedule GROUP BY job_code, scheduled_at HAVING count > 1 ORDER BY scheduled_at;
   ```

1. Zie groepen taken die tegelijkertijd moeten worden uitgevoerd.

<u> Verwacht resultaat </u>: Één kruin `job_code` zou voor de bepaalde tijdspanne moeten worden gepland.

<u> Werkelijk resultaat </u>: Er zijn veelvoudige kroonbanen die voor de zelfde tijdspanne worden gepland.

## Oplossing

Voor Adobe Commerce op de handelaars van de wolkeninfrastructuur, [ zal het bijwerken van de ECE-hulpmiddelen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) de kwestie oplossen.

Adobe Commerce-winkeliers dienen een van de bijgevoegde patches toe te passen om het probleem op te lossen.

## Patches

De patches zijn aan dit artikel gekoppeld. Als u wilt downloaden, gaat u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op een van de volgende koppelingen:

* [Download MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip)
* [Download MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip)
* [MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch downloaden](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* [MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch downloaden](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip)
* [Download MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip)
* [Download MDVA-11304\_EE\_2.2\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip)
* [Download MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip)

### Compatibele Adobe Commerce-versies

De patches zijn gemaakt voor een bepaalde versie die is vermeld in de naam van het patchbestand. MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch is bijvoorbeeld gemaakt voor Adobe Commerce 2.2.4 en is de beste patch voor deze versie.

De patches zijn ook compatibel met de volgende versies:

* Voor Adobe Commerce op-gebouw 2.1.0-2.1.4: [ Download MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch ](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip) Het flard is ook compatibel (maar zou de kwestie niet kunnen oplossen) met de volgende versies en uitgaven van Adobe Commerce:
   * Adobe Commerce op cloudinfrastructuur 2.1.0-2.1.4
* Voor Adobe Commerce op-gebouw 2.1.5-2.1.12: [ Download MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch ](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip) Het flard is ook compatibel (maar zou de kwestie niet kunnen oplossen) met de volgende versies en uitgaven van Adobe Commerce:
   * Adobe Commerce op cloudinfrastructuur 2.1.5-2.1.12
* Voor Adobe Commerce op wolkeninfrastructuur 2.1.13: [ Download MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch ](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* Voor Adobe Commerce op-gebouw 2.1.14-2.1.17: [ Download MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch ](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip) Het flard is ook compatibel (maar kan de kwestie niet oplossen) met de volgende versies en uitgaven van Adobe Commerce:
   * Adobe Commerce op locatie 2.1.18
   * Adobe Commerce op cloudinfrastructuur 2.1.14-2.1.18
* Voor Adobe Commerce op-gebouw 2.2.0-2.2.1: [ Download MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch ](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip) Het flard is ook compatibel (maar zou de kwestie niet kunnen oplossen) met de volgende versies en de uitgaven van Adobe Commerce:
   * Adobe Commerce over cloudinfrastructuur 2.2.0-2.2.1
* Voor Adobe Commerce op-gebouw 2.2.0-2.2.3: [ Download MDVA-11304 \_EE\_2.2\_COMPOSER\_v1.patch ](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip) Het flard is ook compatibel (maar zou de kwestie niet kunnen oplossen) met de volgende versies en de uitgaven van Adobe Commerce:
   * Adobe Commerce over cloudinfrastructuur 2.2.0-2.2.3
* Voor Adobe Commerce op-gebouw 2.2.4: [ Download MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch ](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip) Het flard is ook compatibel (maar zou de kwestie niet kunnen oplossen) met de volgende versies en uitgaven van Adobe Commerce:
   * Adobe Commerce over wolkeninfrastructuur 2.2.4

## Hoe de pleister aanbrengen

Zie [ hoe te om een componentenflard toe te passen die door Adobe Commerce ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze steunkennisbasis, voor instructies wordt verstrekt.

## Bijgevoegde bestanden
