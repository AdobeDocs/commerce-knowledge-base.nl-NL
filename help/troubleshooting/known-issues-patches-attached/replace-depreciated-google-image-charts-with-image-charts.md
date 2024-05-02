---
title: Afgeschreven Google-afbeeldingen vervangen door afbeeldingen
description: De meeste Adobe Commerce-versies en -versies gebruiken momenteel [Google Image Charts] (https://developers.google.com/chart/image/) om statische diagrammen te renderen in Admin-dashboards. Vanaf 14 maart 2019 biedt Google geen ondersteuning meer voor Google Image Charts. Om dit probleem op te lossen, bieden we een patch waarmee we Google Image Charts kunnen vervangen door de gratis service [Image-Charts](https://www.image-charts.com/).
exl-id: f86f0bb9-8a03-471d-8696-1eba4b8acbd1
feature: Cache, Compliance
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Afgeschreven Google-afbeeldingen vervangen door afbeeldingen

De meeste Adobe Commerce-versies en -versies worden momenteel gebruikt [Google-afbeeldingen](https://developers.google.com/chart/image/) om statische grafieken in Admin dashboards terug te geven. Vanaf 14 maart 2019 biedt Google geen ondersteuning meer voor Google Image Charts. Om dit probleem op te lossen, bieden we een patch waarmee we Google Image Charts kunnen vervangen door [Afbeeldingsgrafieken](https://www.image-charts.com/) gratis diensten.

## Betrokken versies

* Adobe Commerce 1.X, alle edities
* Adobe Commerce 2.X, alle edities

>[!NOTE]
>
>Adobe Commerce op locatie 1.14.4.1, Magento Open Source 1.9.4.1, Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.2 zullen deze diagramupdate bevatten. Als u een upgrade uitvoert naar deze versies, wordt de ondersteuning voor afbeeldingsgrafieken zonder extra patches voortgezet.

## Probleem

Google heeft op 14 maart 2019 de ondersteuning van Google Image Charts stopgezet. Gebruikers van Adobe Commerce 1.X en Adobe Commerce 2.2.X kunnen alleen statische diagrammen weergeven als ze de patch downloaden en toepassen en Google Image Charts vervangen door Image-Charts. Weergegeven grafieken hebben hetzelfde ontwerp en dezelfde functionaliteit als Google Image Charts via de gratis accountservice Image-Charts met een [GDPR](https://www.image-charts.com/data-processing-addendum.html) privacybeleid naleven. Zie voor meer opties [Afbeeldingsgrafieken](https://www.image-charts.com/).

## Oplossing

Als u statische diagrammen wilt weergeven in de Commerce Admin, downloadt en past u de patch toe die door Adobe Commerce is meegeleverd. Er is geen aanvullende configuratie nodig.

### Adobe Commerce ter plaatse

1. Sla de [bijgevoegde MAGETWO-98833\_composer\_patch-2019-04-15-04-38-57.patch](assets/MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch.zip) te uploaden naar uw Adobe Commerce-hoofdmap.
1. Voer de volgende opdracht SSH uit, waarbij u de naam van de patch hebt vervangen door de naam van de feitelijke patch:

   ```git
   patch -p1 < MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch
   ```

   Als de bovenstaande opdracht niet werkt, probeert u het `-p2` in plaats van `-p1`.)

1. Vernieuw de cache in Admin onder om de wijzigingen door te voeren **Systeem** > **Cachebeheer**.

### Adobe Commerce over cloudinfrastructuur

Voor Cloud-handelaren wordt de patch opgenomen in de dichtstbijzijnde ECE-tools-update.

### Magento 2 open bron

1. Ga naar [https://magento.com/tech-resources/download\#download2291](https://magento.com/tech-resources/download#download2291).
1. In de **Selecteer uw indeling** vervolgkeuzelijst, selecteert u de componentversie en klikt u op **Downloaden**.
1. Upload de patch naar uw Adobe Commerce-hoofdmap.
1. Voer de volgende opdracht SSH uit, waarbij u de naam van de patch hebt vervangen door de naam van de feitelijke patch:

   ```git
   patch -p1 < MAGETWO-98833_composer_patch-2019-04-15-04-37-48.patch
   ```

   (Als de bovenstaande opdracht niet werkt, probeert u het `-p2` in plaats van `-p1`.)

1. Vernieuw de cache in Admin onder om de wijzigingen door te voeren **Systeem** > **Cachebeheer**.

### Adobe Commerce 1 ter plaatse

Ga als volgt te werk om de patch te downloaden en toe te passen:

1. Sla de [Bijgevoegde MPERF-10509-EE-2019-03-13-06-32-19.diff](assets/MPERF-10509-EE-2019-03-13-06-32-19.diff.zip) te uploaden naar uw Adobe Commerce-hoofdmap.
1. Voer de volgende SSH-opdracht uit:

   ```git
   patch -p1 < MPERF-10509-EE-2019-03-13-06-32-19.diff
   ```

   (Als de bovenstaande opdracht niet werkt, probeert u het `-p2` in plaats van `-p1`.)

1. Vernieuw de cache in Admin onder om de wijzigingen door te voeren **Systeem** > **Cachebeheer**.

### Magento 1 open bron

Ga als volgt te werk om de patch te downloaden en toe te passen:

1. Klikken [**deze koppeling**](https://magento.com/tech-resources/download#download2283) om de patch voor dashboardgrafieken voor beheerders te vinden.
1. Selecteren

   ```git
   MPERF-10509.diff
   ```

   van de **Selecteer uw indeling** en klik op Downloaden.

1. Upload het bestand naar de hoofdmap van Adobe Commerce.
1. Voer de volgende SSH-opdracht uit:

   ```git
   patch -p1 < MPERF-10509.diff
   ```

   (Als de bovenstaande opdracht niet werkt, probeert u het `-p2` in plaats van `-p1`.)

1. Vernieuw de cache in Admin onder om de wijzigingen door te voeren **Systeem** > **Cachebeheer**.

## Bijgevoegde bestanden

[Download MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch](assets/MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch)

[Download MPERF-10509-EE-2019-03-13-06-32-19.diffh](assets/MPERF-10509-EE-2019-03-13-06-32-19.diff)
