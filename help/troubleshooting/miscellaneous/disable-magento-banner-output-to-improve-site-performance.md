---
title: Uitvoer van Adobe Commerce Banner uitschakelen om de prestaties van de site te verbeteren
description: Dit artikel biedt een oplossing voor lage prestaties op de site. De lage plaatsprestaties kunnen worden veroorzaakt door de module ` Magento_Banner' die wordt toegelaten maar niet wordt gebruikt. Als u de uitvoer van de module uitschakelt, kunnen de prestaties van de site verbeteren. Controleer het artikel voor resolutiestappen.
exl-id: 90a8bd21-1f2c-4cfe-8213-17f877e20de8
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Uitvoer van Adobe Commerce Banner uitschakelen om de prestaties van de site te verbeteren

Dit artikel biedt een oplossing voor lage prestaties op de site. Lage prestaties op de site kunnen worden veroorzaakt door de `Magento_Banner` module die wordt ingeschakeld maar niet wordt gebruikt. Als u de uitvoer van de module uitschakelt, kunnen de prestaties van de site verbeteren. Controleer het artikel voor resolutiestappen.

>[!NOTE]
>
>Als u de Adobe Commerce Banner-functionaliteit gebruikt, raadpleegt u de [De hoge productie AJAX verzoeken veroorzaken slechte prestaties](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) artikel in onze basis van de steunkennis voor aanbevelingen over hoe te om prestatieskwesties te vermijden die door bovenmatige verzoeken Ajax worden veroorzaakt.

## Betrokken producten en versies

* Adobe Commerce on cloud Infrastructure v.2.x.x
* Adobe Commerce op locatie v.2.2.x en 2.3.x

## Probleem

De `Magento_Banner` is ingeschakeld, maar wordt niet gebruikt.

Om te controleren of dit het geval is:

Voor Adobe Commerce op cloudinfrastructuur 2.2.x:

1. Meld u aan bij de Commerce-beheerder.
1. Navigeren naar **Inhoud** > *Elementen* > **Banners**.
1. Als het raster dat op deze pagina wordt weergegeven leeg is, hebt u geen banners.

Als u het geneesmiddel niet ziet **Banners** optie onder **Inhoud** > *Elementen* Dat is echter niet het geval en de aanbevelingen uit dit artikel kunnen niet worden toegepast.

Voor Adobe Commerce op cloudinfrastructuur 2.3.x (de functionaliteit was [hernoemd in v 2.3.x](https://devdocs.magento.com/guides/v2.3/release-notes/ReleaseNotes2.3.0Commerce.html#banner-now-dynamic-block)):

1. Meld u aan bij de Commerce-beheerder.
1. Navigeren naar **Inhoud** > *Elements >*  **Dynamische blokken**.
1. Als het raster op deze pagina leeg is, hebt u geen dynamische blokken (banners).

Als u het geneesmiddel niet ziet **Dynamische blokken** optie onder **Inhoud** > *Elementen* Dat is echter niet het geval en de aanbevelingen uit dit artikel kunnen niet worden toegepast.

## Oorzaak

Wanneer de `Magento_Banner` wordt toegelaten, verzendt Adobe Commerce Ajax- verzoeken van de storefront naar de server om de bannerinformatie te krijgen. Deze Ajax-verzoeken hebben een invloed op de prestaties, met name in situaties met een hoge belasting (hoog volume en hoog verkeer). Als de functionaliteit niet wordt gebruikt, wordt geadviseerd dat u de moduleoutput onbruikbaar maakt. Vanwege afhankelijkheidsproblemen wordt het niet aanbevolen de module uit te schakelen.

## Oplossing

>[!WARNING]
>
>We raden u ten zeerste aan wijzigingen te testen op [Staging-/integratieomgeving](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) eerst, alvorens het op Productie toe te passen. We raden u ook aan een recente back-up te maken voordat u iets manipuleert.

1. Schakel het dialoogvenster `Magento_Banner` moduleuitvoer, zoals beschreven in [Uitvoer van module uitschakelen](https://devdocs.magento.com/guides/v2.3/config-guide/config/disable-module-output.html) in onze ontwikkelaarsdocumentatie. De modulenaam u moet gebruiken is `Magento_Banner`.
1. Implementeer uw code. Implementeer voor Adobe Commerce op cloudinfrastructuur zoals beschreven in het dialoogvenster [Je winkel implementeren](https://devdocs.magento.com/guides/v2.3/cloud/live/stage-prod-live.html) artikel in onze ontwikkelaarsdocumentatie.
