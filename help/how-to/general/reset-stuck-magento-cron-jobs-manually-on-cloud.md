---
title: Vastgezette Adobe Commerce handmatig opnieuw instellen op snijtaken in cloudinfrastructuur
description: Adobe Commerce op cloudinfrastructuur is niet klaar met uitvoeren, zit vast en voorkomt dat andere cron-taken worden uitgevoerd. Dit artikel laat zien hoe u de vastgezette uitsnijdtaken handmatig opnieuw kunt instellen.
exl-id: aec6de8e-c3a9-4a6d-8ecd-a213e77c97a1
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Vastgezette Adobe Commerce handmatig opnieuw instellen op snijtaken in cloudinfrastructuur

Adobe Commerce op cloudinfrastructuur is niet klaar met uitvoeren, zit vast en voorkomt dat andere cron-taken worden uitgevoerd. Dit artikel laat zien hoe u de vastgezette uitsnijdtaken handmatig opnieuw kunt instellen.

Wees voorzichtig met deze opdracht! We raden u aan de [Cron-taken opnieuw instellen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html) artikel in onze kennisbasis voor ondersteuning voor meer informatie .

## Stappen

>[!INFO]
>
>Van [ECE-Tools v2002.0.4](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-release-archive.html#v2002.0.4) u kunt vastgezette bouwbanen manueel terugstellen gebruikend een CLI bevel via de toegang van SSH.

1. [SSH voor uw omgeving](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Deze opdracht uitvoeren: `./vendor/bin/ece-tools cron:unlock`

## Waarschuwingen

* De opdracht wordt opnieuw ingesteld **alles** kroonbanen, waaronder die welke momenteel worden uitgevoerd; **alleen in uitzonderlijke gevallen**.
* Gebruik deze oplossing niet als indexeerprogramma&#39;s worden uitgevoerd.

## Lees dit in onze kennisbasis voor support:

[Cron-taken opnieuw instellen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
