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

Als u de tijdvariabelen voor drie geplande taken in Admin bewerkt, wordt de functie voor uitsnijden geconfigureerd om elke minuut te worden uitgevoerd `cron_schedule` de gegevensbestandlijst toont groepen veelvoudige taken die tezelfdertijd worden gepland te lopen.

<u>Stappen om te reproduceren</u>:

1. Navigeer in Commerce Admin naar **Winkels** > Instellingen > **Configuratie** > **GEAVANCEERD** > **Systeem** > **Uitsnijden (geplande taken)** > **Opties voor uitsnijdconfiguratie voor groep: standaard.**
1. Configureer de volgende opties:
   * **Historie opruimen elke**: de **Systeem gebruiken** selectievakje en instellen op *1440*.
   * **Levensduur succesvolle historie**: de **Systeem gebruiken** selectievakje en instellen op *1440*.
   * **Historieperiode mislukt**: de **Systeem gebruiken** selectievakje en instellen op *1440*.

1. Klikken **Config opslaan**.
1. Voer de `crontab -e` gebruiken.
1. Stel de kroon in op elke minuut.
1. Open drie eindtabbladen/vensters.
1. Ga naar de Adobe Commerce `root/base/project` in elk terminalvenster.
1. Voer de volgende opdracht uit in elk tabblad/venster:

   ```bash
   bin/magento cache:flush && bin/magento cron:run && bin/magento cache:flush && bin/magento cron:run
   ```

1. Ga naar MySQL en voer de volgende query uit:

   ```sql
   SELECT job_code, scheduled_at, count as count FROM cron_schedule GROUP BY job_code, scheduled_at HAVING count > 1 ORDER BY scheduled_at;
   ```

1. Zie groepen taken die tegelijkertijd moeten worden uitgevoerd.

<u>Verwacht resultaat</u>: Eén uitsnede `job_code` moeten voor een bepaalde periode worden gepland.

<u>Werkelijk resultaat</u>: Er zijn meerdere snijtaken gepland voor dezelfde periode.

## Oplossing

Voor Adobe Commerce op producten van cloudinfrastructuur, [het bijwerken van de ECE-instrumenten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) zal het probleem oplossen.

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

* Voor Adobe Commerce op locatie 2.1.0-2.1.4: [Download MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip) De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:
   * Adobe Commerce op cloudinfrastructuur 2.1.0-2.1.4
* Voor Adobe Commerce op locatie 2.1.5-2.1.12: [Download MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip) De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:
   * Adobe Commerce op cloudinfrastructuur 2.1.5-2.1.12
* Voor Adobe Commerce op cloud-infrastructuur 2.1.13: [MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch downloaden](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* Voor Adobe Commerce op locatie 2.1.14-2.1.17: [MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch downloaden](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip) De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:
   * Adobe Commerce op locatie 2.1.18
   * Adobe Commerce op cloudinfrastructuur 2.1.14-2.1.18
* Voor Adobe Commerce op locatie 2.2.0-2.2.1: [Download MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip) De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:
   * Adobe Commerce over cloudinfrastructuur 2.2.0-2.2.1
* Voor Adobe Commerce op locatie 2.2.0-2.2.3: [Download MDVA-11304\_EE\_2.2\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip) De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:
   * Adobe Commerce over cloudinfrastructuur 2.2.0-2.2.3
* Voor Adobe Commerce op locatie 2.2.4: [Download MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip) De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:
   * Adobe Commerce over wolkeninfrastructuur 2.2.4

## Hoe de pleister aanbrengen

Zie [Een door Adobe Commerce geleverde componentpatch toepassen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze kennisbasis voor ondersteuning, voor instructies.

## Bijgevoegde bestanden
