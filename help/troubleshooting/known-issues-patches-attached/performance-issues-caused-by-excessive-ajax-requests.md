---
title: Prestatieproblemen veroorzaakt door buitensporige Ajax-aanvragen
description: Dit artikel bevat een patch voor het bekende Adobe Commerce-prestatieprobleem dat wordt veroorzaakt door excessieve Ajax-aanvragen. Het probleem is opgelost in Adobe Commerce 2.3.4.
exl-id: d9a69406-3970-4556-aa6a-1309b24366d8
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Prestatieproblemen veroorzaakt door buitensporige Ajax-aanvragen

Dit artikel bevat een patch voor het bekende Adobe Commerce-prestatieprobleem dat wordt veroorzaakt door excessieve Ajax-aanvragen. Het probleem is opgelost in Adobe Commerce 2.3.4.

## Probleem

Adobe Commerce zou overtollige [ verzoeken van Ajax ](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) van de storefront naar de server kunnen verzenden om de bannerinformatie en klanteninformatie te krijgen. Deze Ajax-verzoeken hebben een invloed op de prestaties, met name in situaties met een hoge belasting (hoog volume en hoog verkeer). Zo als de functionaliteit van de Banner niet wordt gebruikt, adviseert men dat u volledig [ de de moduleoutput van de Banner van Adobe Commerce ](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md) onbruikbaar maakt en het flard toepast om het terugwinnen van klanteninformatie te verbeteren.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[Download de MDVA-24597\_EE\_2.2.9\_COMPOSER\_v1.patch](assets/MDVA-24597_EE_2.2.9_COMPOSER_v1.patch.zip)

### Compatibele Adobe Commerce-versies

De patch is geldig voor de volgende producten en versies:

* Adobe Commerce over cloudinfrastructuur 2.2.9
* Adobe Commerce op locatie 2.2.9

Als u een andere versie van Adobe Commerce hebt, kunt u het bijwerken naar de nieuwste versie van 2.3.x overwegen. Als dit momenteel geen optie is, gelieve [ de Steun van Adobe Commerce ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) te contacteren en een flard voor uw versie te verzoeken.

## Hoe de pleister aanbrengen

Zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies wordt verstrekt.

## Bijgevoegde bestanden
