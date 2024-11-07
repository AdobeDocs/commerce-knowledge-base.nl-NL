---
title: '"[!DNL Live Search] toont uit-van-voorraadproducten ongeacht de montages van de voorraadstatus in admin.'
description: In dit artikel wordt informatie gegeven over het bekende probleem waarbij op de pagina met productaanbiedingen (PLP) de *We kunnen geen producten vinden die overeenkomen met de fout in de selectie* terwijl de zoekkeuzelijst sommige items retourneert.
exl-id: 2a351b83-407c-444a-a761-4932b5b88843
feature: Admin Workspace, Categories, Orders, Products, Search
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# [!DNL Live Search] geeft producten uit de voorraad weer, ongeacht de statusinstellingen van de voorraad in de beheerder

>[!IMPORTANT]
>
>Dit probleem is opgelost in [[!DNL Live Search]  [2.0.4] ](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html). Om de recentste versie te installeren, verwijs naar [ Bijwerkend  [!DNL Live Search] ](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#update) in de gebruikersgids.

Dit artikel verstrekt informatie over de bekende kwestie waar het Product van de Lijst van de Pagina (PLP) *toont wij geen producten kunnen vinden die de selectie* fout aanpassen terwijl onderzoekspopover sommige punten terugkeert.

## Betrokken producten en versies

Adobe Commerce (alle implementatiemethoden) 2.4.x

## Probleem

[!DNL Live Search] geeft zoekresultaten weer ongeacht de statusinstellingen van de voorraad in Adobe Commerce Admin. Zelfs wanneer **[!UICONTROL Display Out-of-Stock Products]** aan *Nr* wordt geplaatst, worden de producten getoond. Het resulteert in de fout PLP *wij kunnen geen producten vinden die de selectie* aanpassen.

<u> Stappen om </u> te reproduceren:

1. Maak een categorie en voeg producten toe. (Voorbeeld: Categorie = _Jeans_, Product1 = _Blauwe Jeans_, Product2 = _Zwarte Jeans_)
1. Maak alle producten in de categorie uit voorraad.
1. Plaats **[!UICONTROL Display Out-of-Stock Products]** aan *Nr*.
1. Op de storefront, ga *Jeans* op het onderzoeksgebied in.
1. Klik op **[!UICONTROL View All]** in het pop-upmenu.

<u> Verwacht resultaat </u>:

U ziet *wij kunnen geen producten vinden die het selectie* bericht op PLP aanpassen, en geen producten worden getoond op het onderzoek pop-up.

<u> Werkelijk resultaat </u>:

U ziet *wij kunnen geen producten vinden die het selectie* bericht op PLP aanpassen, en beide producten worden getoond op het onderzoek pop-up.

## Oplossing

Op dit moment is er geen oplossing voor deze kwestie. Ons team van [!DNL Live Search] zal binnenkort een instelling opgeven om [!DNL Live Search] zodanig te configureren dat producten correct worden weergegeven.

## Gerelateerde lezing

[ installeer  [!DNL Live Search] ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install) in onze gebruikersgids.
