---
title: Uitvoer van Adobe Commerce Banner uitschakelen om de prestaties van de site te verbeteren
description: Dit artikel biedt een oplossing voor lage prestaties op de site. De lage plaatsprestaties kunnen worden veroorzaakt door de module ` Magento_Banner wordt toegelaten maar niet gebruikt. Als u de uitvoer van de module uitschakelt, kunnen de prestaties van de site verbeteren. Controleer het artikel voor resolutiestappen.
exl-id: 90a8bd21-1f2c-4cfe-8213-17f877e20de8
feature: Configuration
role: Developer
source-git-commit: 76ef59dc37504f50d55734a90c9ce5b30bb83175
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Uitvoer van Adobe Commerce Banner uitschakelen om de prestaties van de site te verbeteren

Dit artikel biedt een oplossing voor lage prestaties op de site. Lage siteprestaties kunnen worden veroorzaakt door het inschakelen van de module `Magento_Banner` , maar niet door het gebruik ervan. Als u de uitvoer van de module uitschakelt, kunnen de prestaties van de site verbeteren. Controleer het artikel voor resolutiestappen.

>[!NOTE]
>
>Als u de functionaliteit van de Banner van Adobe Commerce gebruikt, zie de [ Hoge vraag van de productieAJAX slechte prestaties ](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) artikel in onze steunkennisbasis voor aanbevelingen op hoe te om prestatieskwesties te vermijden die door bovenmatige verzoeken van Ajax worden veroorzaakt.

## Betrokken producten en versies

* Adobe Commerce on cloud Infrastructure v.2.x.x
* Adobe Commerce op locatie v.2.2.x en 2.3.x

## Probleem

De module `Magento_Banner` is ingeschakeld, maar wordt niet gebruikt.

Om te controleren of dit het geval is:

Voor Adobe Commerce op cloudinfrastructuur 2.2.x:

1. Meld u aan bij de Commerce-beheerder.
1. Navigeer naar **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Banners]** .
1. Als het raster dat op deze pagina wordt weergegeven leeg is, hebt u geen banners.

Als de optie **[!UICONTROL Banners]** niet wordt weergegeven onder **[!UICONTROL Content]** > **[!UICONTROL Elements]** , betekent dit dat u de aanbevelingen uit dit artikel al hebt toegepast.

Voor Adobe Commerce op wolkeninfrastructuur 2.3.x en nieuwer (de functionaliteit werd anders genoemd [ in v 2.3.x ](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/ReleaseNotes2.3.0Commerce.html#banner-now-dynamic-block)):

1. Meld u aan bij de Commerce-beheerder.
1. Navigeer naar **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Dynamic Blocks]** .
1. Als het raster op deze pagina leeg is, hebt u geen dynamische blokken (banners).

Als de optie **[!UICONTROL Dynamic Blocks]** niet wordt weergegeven onder **[!UICONTROL Content]** > **[!UICONTROL Elements]** , betekent dit dat u de aanbeveling uit dit artikel al hebt toegepast. Als u de banneroptie weer wilt zien, keert u het proces om.

## Oorzaak

Wanneer de module `Magento_Banner` is ingeschakeld, stuurt Adobe Commerce Ajax-aanvragen van de storefront naar de server om de bannergegevens op te halen. Deze Ajax-verzoeken hebben een invloed op de prestaties, met name in situaties met een hoge belasting (hoog volume en hoog verkeer). Als de functionaliteit niet wordt gebruikt, wordt geadviseerd dat u de moduleoutput onbruikbaar maakt. Vanwege afhankelijkheidsproblemen wordt het niet aanbevolen de module uit te schakelen.

## Oplossing

>[!WARNING]
>
>Wij adviseren sterk testende veranderingen op [ het Staging/het milieu van de Integratie ](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) eerst, alvorens het op Productie toe te passen. We raden u ook aan een recente back-up te maken voordat u iets manipuleert.

1. Maak de `Magento_Banner` moduleoutput, zoals die in [ wordt beschreven onbruikbaar moduleoutput ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/disable-module-output) in onze ontwikkelaarsdocumentatie. De modulenaam u moet gebruiken is `Magento_Banner`.
1. Implementeer uw code. Voor Adobe Commerce op wolkeninfrastructuur, stel zoals die in [ wordt beschreven uw opslag ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production) artikel in onze ontwikkelaarsdocumentatie op.
1. Nadat u de uitvoer van de module hebt uitgeschakeld, wordt het menu niet meer weergegeven in de beheerder.
1. U ziet de optie Banner of Dynamisch niet meer onder **[!UICONTROL Content]** > **[!UICONTROL Elements]** . Om de opties opnieuw te tonen, [ laat de moduleoutput ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/disable-module-output?lang=en#disable-module-output-in-a-simple-deployment) toe.

