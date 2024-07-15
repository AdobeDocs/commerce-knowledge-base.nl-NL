---
title: Adobe Commerce  [!DNL crons]  gehandicapt zonder interventie
description: Gebruik dit artikel om de kwestie te bevestigen waar  [!DNL crons]  zonder interventie wordt onbruikbaar gemaakt.
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 9cd7cabc37c0f290c41f790b0fb06177c3156d48
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Adobe Commerce zonder tussenkomst

Dit artikel biedt een oplossing voor het geval [!DNL crons] zonder tussenkomst wordt uitgeschakeld.

## Betrokken producten en versies

* Adobe Commerce op wolkeninfrastructuur, alle [ gesteunde versies ](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Probleem

Uw [!DNL crons] wordt na de implementatie uitgeschakeld.

<u> Stappen om </u> te reproduceren:

Implementeren.

<u> Verwacht resultaat </u>:

Uw [!DNL crons] wordt uitgevoerd.

<u> Werkelijk resultaat </u>:

Uw [!DNL crons] wordt na de implementatie uitgeschakeld.

## Oorzaak

Een probleem met de [!DNL OPcache] -instellingen.

## Oplossing

Bevorder [!DNL ECE Tools] aan de recentste versie [ 2002.1.13 ](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html#v2002113).

## Gerelateerde lezing

* [ Trage prestaties, langzaam en lang lopend  [!DNL crons] ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.html) in onze basis van de steunkennis.
* [[!DNL Cron]  taken vergrendelen taken van andere groepen ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=en) in onze basis van steunkennis.
* [[!DNL Cron]  baan is geplakt in &quot;lopende&quot;status ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) in onze basis van steunkennis.
