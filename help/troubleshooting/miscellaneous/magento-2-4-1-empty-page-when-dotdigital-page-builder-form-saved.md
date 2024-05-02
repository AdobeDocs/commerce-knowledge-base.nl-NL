---
title: "Adobe Commerce 2.4.1: lege pagina wanneer het formulier dotdigital Page Builder is opgeslagen"
description: Dit artikel biedt een oplossing voor een bekend probleem in Adobe Commerce 2.4.1, waarin u een lege webpagina kunt weergeven nadat u een formulier met een digitale pagina hebt opgeslagen in het deelvenster Beheer wanneer u de Safari-browser gebruikt.
exl-id: 682eac73-1ad2-4093-acfb-6a8da4c05cf5
feature: Page Builder
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
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

<u>Stappen om te reproduceren</u>

1. Ga naar **Deelvenster Beheer** > **Inhoud** > **Pagina&#39;s** en selecteert u **Bewerken** van een willekeurige pagina.
1. Ga naar **Inhoud** en klik op de knop **Bewerken met Page Builder** knop.
1. Sleep de **dotdigitaal formulier** blokkeren en selecteren **Bewerken**.
1. Selecteer een van de testformulieren en kies **Ingesloten** en slaat u het formulier op.
1. Sla de paginawijziging op.

<u>Verwacht resultaat:</u>

De webpagina moet zijn opgeslagen.

<u>Werkelijk resultaat:</u>

De webpagina is leeg. Nadat u de webpagina opnieuw hebt geladen, worden de wijzigingen toegepast.

## Workaround

De oplossing is een alternatieve browser te gebruiken voor Safari. Het probleem wordt in de volgende release, Adobe Commerce 2.4.2, in het eerste kwartaal van 2021 opgelost.

## Gerelateerde lezing

* [Wat is Page Builder?](https://devdocs.magento.com/page-builder/docs/) in onze ontwikkelaarsdocumentatie.
* [Pagina Builder instellen](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/setup.html) in onze ontwikkelaarsdocumentatie.
* [Page Builder](https://docs.magento.com/user-guide/cms/page-builder.html) in onze gebruikershandleiding.
* [Page Builder - Elements](https://docs.magento.com/user-guide/cms/page-builder-elements.html) in onze gebruikershandleiding.
