---
title: '[!DNL Live Search] dashboard and search result ranking is incorrect'
description: Dit artikel verstrekt het oplossen van problemeninformatie als de gegevens in het  [!DNL Live Search]  dashboard onjuist zijn, of als het rangschikken van de onderzoeksresultaten niet is wat u verwacht.
feature: Admin Workspace, Categories, Search
role: Developer
source-git-commit: 4c1199c31f83d7c2aaf28e259d63473779bf2efe
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# [!DNL Live Search] dashboard- en zoekresultaatpositie zijn onjuist

Als u opmerkt dat de gegevens die in het [!DNL Live Search] dashboard worden getoond onjuist zijn, of als [ het rangschikken van de onderzoeksresultaten ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/category-merch#ranking-strategies) niet zijn wat u verwacht, zie het volgende om mogelijke redenen:

* Het veld `topLevelSku` van de productcontext in `productView` -gebeurtenissen ontbreekt. Dit veroorzaakt lege omzettingen en andere onverwachte metriek.

* Voor de gebeurtenis `add-to-cart` is het veld `productContext` niet ingesteld en gevuld.

* Het omgevingstype is onjuist. Als de omgeving bijvoorbeeld is ingesteld op *[!UICONTROL Testing]* in plaats van op *[!UICONTROL Production]* . Zie {de context van 0} Storefront ](https://github.com/adobe/commerce-events/blob/main/examples/events/example-contexts/mock-storefront-context.md) voor meer informatie.[

* De context van onderzoeksresultaten mist van [ onderzoek-product-klik ](https://github.com/adobe/commerce-events/blob/main/examples/events/search-product-click.md) gebeurtenis.
