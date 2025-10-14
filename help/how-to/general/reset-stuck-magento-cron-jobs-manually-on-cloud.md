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

Wees voorzichtig met deze opdracht! Wij adviseren lezend het [&#x200B; Uitsnijdbanen van het Terugstellen &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=nl-NL) artikel in onze basis van steunkennis voor meer details.

## Stappen

>[!INFO]
>
>Van [&#x200B; ECE-Hulpmiddelen v2002.0.4 &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-release-archive.html?lang=nl-NL#v2002.0.4) kunt u vastgezette bouwbanen manueel terugstellen gebruikend een CLI bevel via de toegang van SSH.

1. [&#x200B; SSH aan uw milieu &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=nl-NL).
1. Deze opdracht uitvoeren: `./vendor/bin/ece-tools cron:unlock`

## Waarschuwingen

* Het bevel stelt **alle** kron banen, met inbegrip van die momenteel in werking; **gebruikt het in uitzonderlijke gevallen slechts**.
* Gebruik deze oplossing niet als indexeerprogramma&#39;s worden uitgevoerd.

## Lees dit in onze kennisbasis voor support:

[&#x200B; de banen van het Terugstellen cron &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=nl-NL)
