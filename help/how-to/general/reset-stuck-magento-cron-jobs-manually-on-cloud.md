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

Wees voorzichtig met deze opdracht! Wij adviseren lezend het [ Uitsnijdbanen van het Terugstellen ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html) artikel in onze basis van steunkennis voor meer details.

## Stappen

>[!INFO]
>
>Van [ ECE-Hulpmiddelen v2002.0.4 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-release-archive.html#v2002.0.4) kunt u vastgezette bouwbanen manueel terugstellen gebruikend een CLI bevel via de toegang van SSH.

1. [ SSH aan uw milieu ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Deze opdracht uitvoeren: `./vendor/bin/ece-tools cron:unlock`

## Waarschuwingen

* Het bevel stelt **alle** kron banen, met inbegrip van die momenteel in werking; **gebruikt het in uitzonderlijke gevallen slechts**.
* Gebruik deze oplossing niet als indexeerprogramma&#39;s worden uitgevoerd.

## Lees dit in onze kennisbasis voor support:

[ de banen van het Terugstellen cron ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
