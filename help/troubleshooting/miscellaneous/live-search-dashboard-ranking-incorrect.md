---
title: '[!DNL Live Search] dashboard- en zoekresultaatpositie zijn onjuist'
description: Dit artikel verstrekt het oplossen van problemeninformatie als de gegevens in het  [!DNL Live Search]  dashboard onjuist zijn, of als het rangschikken van de onderzoeksresultaten niet is wat u verwacht.
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: d4aea1f1-c2c4-45e5-87c8-73069f7c9ffd
source-git-commit: 9bb839292a120a3dab5151d493f915619dbf5c06
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# [!DNL Live Search] dashboard- en zoekresultaatpositie zijn onjuist

Als u opmerkt dat de gegevens die in het [!DNL Live Search] dashboard worden getoond onjuist zijn, of als [&#x200B; het rangschikken van de onderzoeksresultaten &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-merchant-services/live-search/live-search-admin/category-merch#ranking-strategies) niet zijn wat u verwacht, zie het volgende om mogelijke redenen:

* Het veld `topLevelSku` van de productcontext in `productView` -gebeurtenissen ontbreekt. Dit veroorzaakt lege omzettingen en andere onverwachte metriek.

* Voor de gebeurtenis `add-to-cart` is het veld `productContext` niet ingesteld en gevuld.

* Het omgevingstype is onjuist. Als de omgeving bijvoorbeeld is ingesteld op *[!UICONTROL Testing]* in plaats van op *[!UICONTROL Production]* . Zie {de context van 0} Storefront [&#128279;](https://github.com/adobe/commerce-events/blob/main/examples/events/example-contexts/mock-storefront-context.md) voor meer informatie.

* De context van onderzoeksresultaten mist van [&#x200B; onderzoek-product-klik &#x200B;](https://github.com/adobe/commerce-events/blob/main/examples/events/search-product-click.md) gebeurtenis.
