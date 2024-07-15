---
title: '[!DNL Advanced Reporting] 404 error on Adobe Commerce'
description: Dit artikel biedt een patch voor de Adobe Commerce-uitgave wanneer een handelaar een fout van 404 krijgt wanneer hij probeert toegang te krijgen tot [[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html). Nadat dit flard wordt geïnstalleerd, zullen de gebruikers tot  [!DNL Advanced Reporting] kunnen toegang hebben.
exl-id: bac61704-44fe-4bd2-b342-af90219231ef
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# [!DNL Advanced Reporting] 404-fout op Adobe Commerce

Dit artikel verstrekt een flard voor de kwestie van Adobe Commerce wanneer een handelaar een fout 404 krijgt wanneer zij proberen om tot [[!DNL Advanced Reporting] toegang te hebben ](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html). Nadat deze patch is geïnstalleerd, kunnen gebruikers [!DNL Advanced Reporting] openen.

Als u wilt controleren of deze patch dit probleem kan oplossen, controleert u eerst de logbestanden met de volgende opdracht:

`zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz`

Als u de fout `Not valid cipher` ziet, past u de bijgevoegde patch toe.

## Betrokken producten en versies

Adobe Commerce 2.2.6

## Probleem

Een handelaar krijgt een fout van 404 wanneer zij proberen om tot [!DNL Advanced Reporting] toegang te hebben.

## Oplossing

Als u het probleem wilt verhelpen, past u de patch toe die aan dit artikel is gekoppeld. Om het te downloaden, scrol neer aan het eind van het artikel en klik het dossier - noem, of klik de volgende verbinding: [ Download mDVA-18980 \_EE \_2.2.6\_COMPOSER\_v1 ](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)

## Hoe de pleister aanbrengen

Zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies wordt verstrekt.

## Bijgevoegde bestanden
