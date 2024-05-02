---
title: '[!DNL Live Search] geeft producten uit de voorraad weer, ongeacht de instellingen voor de voorraadstatus in de beheerder.'
description: In dit artikel wordt informatie gegeven over het bekende probleem waarbij op de pagina met productaanbiedingen (PLP) de *We kunnen geen producten vinden die overeenkomen met de fout in de selectie* terwijl de zoekkeuzelijst sommige items retourneert.
exl-id: 2a351b83-407c-444a-a761-4932b5b88843
feature: Admin Workspace, Categories, Orders, Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# [!DNL Live Search] geeft producten uit de voorraad ongeacht de montages van de voorraadstatus in admin weer

>[!IMPORTANT]
>
>Dit probleem is opgelost in [[!DNL Live Search] [2.0.4]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html). Als u de meest recente versie wilt installeren, raadpleegt u [Bijwerken [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#update) in de gebruikershandleiding.

Dit artikel bevat informatie over de bekende kwestie waarop de pagina met productaanbiedingen (Product Listing Page, PLP) de *Er zijn geen producten gevonden die overeenkomen met de selectie* Er is een fout opgetreden terwijl de zoekpop-up sommige items retourneert.

## Betrokken producten en versies

Adobe Commerce (alle implementatiemethoden) 2.4.x

## Probleem

[!DNL Live Search] geeft zoekresultaten weer, ongeacht de instellingen voor de voorraadstatus in Adobe Commerce Admin. Zelfs als de **[!UICONTROL Display Out-of-Stock Products]** is ingesteld op *Nee*, worden de producten weergegeven. Dit resulteert in de PLP-fout *Er zijn geen producten gevonden die overeenkomen met de selectie*.

<u>Stappen om te reproduceren</u>:

1. Maak een categorie en voeg producten toe. (Voorbeeld: Categorie = _Jeans_, Product1 = _Blauwe jood_, Product2 = _Zwarte Jeans_)
1. Maak alle producten in de categorie uit voorraad.
1. Set **[!UICONTROL Display Out-of-Stock Products]** tot *Nee*.
1. Voer in de winkel *Jeans* in het zoekveld.
1. Klikken **[!UICONTROL View All]** in het pop-upvenster.

<u>Verwacht resultaat</u>:

U ziet de *Er zijn geen producten gevonden die overeenkomen met de selectie* bericht op PLP, en geen producten worden getoond op het onderzoek pop-up.

<u>Werkelijk resultaat</u>:

U ziet de *Er zijn geen producten gevonden die overeenkomen met de selectie* bericht op PLP, en beide producten worden getoond op het onderzoek pop-up.

## Oplossing

Op dit moment is er geen oplossing voor deze kwestie. Ons [!DNL Live Search] team zal spoedig plaatsen verstrekken om te vormen [!DNL Live Search] om producten correct weer te geven.

## Gerelateerde lezing

[Installeren [!DNL Live Search]](https://docs.magento.com/user-guide/live-search/install.html) in onze gebruikershandleiding.
