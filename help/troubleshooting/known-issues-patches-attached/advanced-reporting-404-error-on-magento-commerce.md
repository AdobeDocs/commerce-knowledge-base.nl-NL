---
title: '[!DNL Advanced Reporting] 404 error on Adobe Commerce'
description: Dit artikel bevat een patch voor de Adobe Commerce-uitgave wanneer een handelaar een fout van 404 krijgt wanneer hij probeert toegang te krijgen tot [[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html). Nadat deze patch is geïnstalleerd, kunnen gebruikers [!DNL Advanced Reporting].
exl-id: bac61704-44fe-4bd2-b342-af90219231ef
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# [!DNL Advanced Reporting] 404-fout op Adobe Commerce

Dit artikel bevat een patch voor de Adobe Commerce-uitgave wanneer een handelaar een fout van 404 krijgt wanneer hij of zij toegang probeert te krijgen [[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html). Nadat deze patch is geïnstalleerd, kunnen gebruikers [!DNL Advanced Reporting].

Als u wilt controleren of deze patch dit probleem kan oplossen, controleert u eerst de logbestanden met de volgende opdracht:

`zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz`

Als u de `Not valid cipher` fout, pas de bijgevoegde patch toe.

## Betrokken producten en versies

Adobe Commerce 2.2.6

## Probleem

Een handelaar krijgt een fout van 404 wanneer zij proberen toegang te hebben [!DNL Advanced Reporting].

## Oplossing

Als u het probleem wilt verhelpen, past u de patch toe die aan dit artikel is gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling: [Download MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)

## Hoe de pleister aanbrengen

Zie [Hoe een door Adobe geleverde componentpleister aanbrengen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies.

## Bijgevoegde bestanden
