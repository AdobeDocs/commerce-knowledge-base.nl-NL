---
title: '[!DNL Cron] -taak is vastgelopen in de status **running**'
description: Dit artikel verstrekt oplossingen voor wanneer de banen van Adobe Commerce  [!DNL cron]  niet voltooien uitvoerend en in een "lopende"status voortzetten, die andere  [!DNL cron]  banen verhindert te lopen. Dit kan om een aantal redenen, zoals netwerkkwesties, toepassingsneerstortingen, re-plaatsingskwesties gebeuren.
exl-id: 11e01a2b-2fcf-48c2-871c-08f29cd76250
feature: Configuration
role: Developer
source-git-commit: 08a241131453725a86eda5f267a209e6705da2e3
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# [!DNL Cron] -taak blijft vastzitten in de status &quot;actief&quot;

Dit artikel biedt oplossingen voor het feit dat Adobe Commerce [!DNL cron] -taken niet zijn voltooid en in de status &quot;actief&quot; blijven, waardoor andere [!DNL cron] -taken niet kunnen worden uitgevoerd. Dit kan om een aantal redenen, zoals netwerkkwesties, toepassingsneerstortingen, re-plaatsingskwesties gebeuren.

## Betrokken producten en versies

Adobe Commerce op cloud-infrastructuur, alle versies

## Symptoom {#symptom}

Symptomen van [!DNL cron] -taken die opnieuw moeten worden ingesteld zijn:

* Er wordt een groot aantal taken weergegeven in de `cron_schedule` -wachtrij
* De prestaties van de site gaan achteruit
* Taken worden niet volgens schema uitgevoerd

## Oplossingen {#solutions}

### Oplossing om alle [!DNL cron] taken tegelijk te stoppen {#solution-stop-all-crons-at-once}

>[!WARNING]
>
>Het in werking stellen van dit bevel zonder de `--job-code` optie stelt *alle* [!DNL cron] banen, met inbegrip van die momenteel in werking, zodat adviseren wij gebruikend het slechts in uitzonderlijke gevallen, zoals nadat u hebt geverifieerd dat alle [!DNL cron] banen moeten worden teruggesteld. Herimplementatie voert deze opdracht standaard uit om [!DNL cron] -taken opnieuw in te stellen, zodat ze op de juiste wijze worden hersteld nadat de omgeving weer is hersteld. Gebruik deze oplossing niet als indexeerprogramma&#39;s worden uitgevoerd.

U kunt dit probleem oplossen door de [!DNL cron] taak(en) opnieuw in te stellen met de opdracht `cron:unlock` . Met deze opdracht wijzigt u de status van de [!DNL cron] -taak in de database, waardoor de taak gedwongen wordt om andere geplande taken te laten doorgaan.

1. Open een terminal en gebruik uw [ sleutels van SSH ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) om met het beïnvloede milieu te verbinden.
1. Krijg de MySQL gegevensbestandgeloofsbrieven:    ```shell    echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp    ```
1. Verbind met het gegevensbestand gebruikend `mysql`:    ```shell    mysql -hdatabase.internal -uuser -ppassword main    ```
1. Selecteer de `main` -database:    ```shell    use main    ```
1. Alle actieve [!DNL cron] taken zoeken:    ```shell    SELECT * FROM cron_schedule WHERE status = 'running';    ```
1. Kopieer de `job_code` van elke taak die langer dan normaal wordt uitgevoerd.
1. Gebruik de schema-id&#39;s van de vorige stap om specifieke [!DNL cron] -taken te ontgrendelen:    ```shell    ./vendor/bin/ece-tools cron:unlock --job-code=<job_code_1> [... --job-code=<job_code_x>]    ```

### Oplossing voor het stoppen van één oplossing [!DNL cron] {#solution-stop-a-single-cron}

1. Open een terminal en gebruik uw [ sleutels van SSH ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) om met het beïnvloede milieu te verbinden.
1. Controleer lange lopende taken door het volgende bevel te gebruiken:

   ```date; ps aux | grep '[%]CPU\|cron\|magento\|queue' | grep -v 'grep\|cron -f'```

1. In de output, zoals in de steekproefoutput hieronder, zult u huidige datum en lijst van processen zien. In de kolom `START` wordt de begintijd of -datum van het proces weergegeven:

   ```
   Wed May  8 22:41:31 UTC 2019
   USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
   root       590  0.0  0.0  27528  2768 ?        Ss   Jan15   0:49 /usr/sbin/cron -f
   bxc2qly+ 25855  0.0  0.0  23724  2184 ?        S    20:51   0:00 logger -d -u /run/bxc2qlykqhbqe_stg-cron.sock -p cron.info -s -t cron-bxc2qlykqhbqe_stg-bxc2qlykqhbqe_stg
   bxc2qly+ 25860 57.7  1.3 584220 222692 ?       S    20:51   0:02 php bin/magento cron:run
   bxc2qly+ 25863  0.0  0.0  23724  2472 ?        S    20:51   0:00 logger -d -u /run/bxc2qlykqhbqe-cron.sock -p cron.info -s -t cron-bxc2qlykqhbqe-bxc2qlykqhbqe
   bxc2qly+ 25876 53.0  0.6 475472 111468 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25878 57.0  0.6 475472 112080 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=staging --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25880 50.5  0.6 475472 111312 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=catalog_event --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25882 48.5  0.6 475472 111220 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=consumers --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25884 50.5  0.6 475472 111372 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=ddg_automation --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25890 32.5  0.6 475368 110672 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=staging --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25892 34.5  0.6 475472 110724 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=catalog_event --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25894 31.5  0.6 475368 110136 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=consumers --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25896 29.0  0.6 475320 109876 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=ddg_automation --bootstrap=standaloneProcessStarted=1
   ```

1. Als u lange [!DNL cron] banen ziet die het proces van de blokplaatsing kunnen, kunt u het proces beëindigen gebruikend het `kill` bevel. U kunt **identiteitskaart van het Proces** identificeren (vond de `PID` kolom), en dan zetten dat `PID` in het bevel om het proces te doden.
Het **bevel van het het processen van de doden** is:

   ```kill -9 <PID>```

1. Dan kunt u heropstellen, als u probeerde om opnieuw op te stellen.
