---
title: Adobe Commerce [!DNL crons] uitgeschakeld zonder tussenkomst
description: Met dit artikel kunt u het probleem oplossen waarbij [!DNL crons] zijn uitgeschakeld zonder tussenkomst.
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 9cd7cabc37c0f290c41f790b0fb06177c3156d48
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Adobe Commerce zonder tussenkomst

Dit artikel biedt een oplossing voor wanneer [!DNL crons] zijn uitgeschakeld zonder tussenkomst.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, alle [ondersteunde versies](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Probleem

Uw [!DNL crons] worden uitgeschakeld na de implementatie.

<u>Stappen om te reproduceren</u>:

Implementeren.

<u>Verwacht resultaat</u>:

Uw [!DNL crons] worden uitgevoerd.

<u>Werkelijk resultaat</u>:

Uw [!DNL crons] worden uitgeschakeld na de implementatie.

## Oorzaak

Een probleem met de [!DNL OPcache] instellingen.

## Oplossing

Upgrade [!DNL ECE Tools] naar de meest recente versie [2002 1,13](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html#v2002113).

## Gerelateerde lezing

* [Trage prestaties, traag en lang [!DNL crons]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.html) in onze kennisbasis voor ondersteuning.
* [[!DNL Cron] taken vergrendelen van andere groepen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=en) in onze kennisbasis voor ondersteuning.
* [[!DNL Cron] taak zit vast in status &quot; actief &quot;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) in onze kennisbasis voor ondersteuning.
