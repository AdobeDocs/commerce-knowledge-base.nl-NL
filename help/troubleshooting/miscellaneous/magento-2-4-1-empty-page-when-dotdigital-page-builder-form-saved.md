---
title: 'Adobe Commerce 2.4.1: lege pagina wanneer digitale pagina Builder-formulier wordt opgeslagen'
description: Dit artikel biedt een oplossing voor een bekend probleem in Adobe Commerce 2.4.1, waarin u een lege webpagina kunt weergeven nadat u een formulier met een digitale pagina hebt opgeslagen in het deelvenster Beheer wanneer u de Safari-browser gebruikt.
exl-id: 682eac73-1ad2-4093-acfb-6a8da4c05cf5
feature: Page Builder
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Adobe Commerce 2.4.1: lege pagina wanneer digitale pagina Builder-formulier wordt opgeslagen

Dit artikel biedt een oplossing voor een bekend probleem in Adobe Commerce 2.4.1, waarin u een lege webpagina kunt weergeven nadat u een formulier met een digitale pagina hebt opgeslagen in het deelvenster Beheer wanneer u de Safari-browser gebruikt.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.1
* Adobe Commerce over wolkeninfrastructuur 2.4.1

## Probleem

<u> Stappen om te reproduceren </u>

1. Ga naar **Comité Admin** > **Inhoud** > **Pagina&#39;s**, en selecteer **uitgeven** van om het even welke pagina.
1. Ga naar **Inhoud** en klik op **uitgeven met de knoop van de Bouwer van de Pagina**.
1. Sleep het **dotdigital vormblok** en selecteer **uitgeven**.
1. Selecteer één van de testvormen, dan kies **Ingebedde** wijze en sparen de vorm.
1. Sla de paginawijziging op.

<u> Verwacht resultaat:</u>

De webpagina moet zijn opgeslagen.

<u> Ware resultaat:</u>

De webpagina is leeg. Nadat u de webpagina opnieuw hebt geladen, worden de wijzigingen toegepast.

## Workaround

De oplossing is een alternatieve browser te gebruiken voor Safari. Het probleem wordt in de volgende release, Adobe Commerce 2.4.2, in het eerste kwartaal van 2021 opgelost.

## Gerelateerde lezing

* [ wat is de Bouwer van de Pagina?](https://developer.adobe.com/commerce/frontend-core/page-builder/) in de documentatie voor ontwikkelaars.
* [ Opstelling van de Bouwer van de Pagina ](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/setup.html) in onze ontwikkelaarsdocumentatie.
* [ Bouwer van de Pagina ](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/introduction) in onze gebruikersgids.
* [ de Bouwer van de Pagina - Elementen ](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/workspace#elements) in onze gebruikersgids.
