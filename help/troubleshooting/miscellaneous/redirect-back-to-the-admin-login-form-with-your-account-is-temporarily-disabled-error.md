---
title: '''Omleiden naar het [!UICONTROL Commerce Admin] -aanmeldingsformulier met de fout ''Uw account is tijdelijk uitgeschakeld'''
description: 'Dit artikel biedt de mogelijke oplossingen voor het aanmeldingsprobleem van Commerce Admin, waarbij u weer naar het aanmeldingsformulier wordt omgeleid met het volgende foutbericht: *"Uw account is tijdelijk uitgeschakeld"*. De voorgestelde oplossing controleert en verbetert de montages van het admin gebruikersgegevensbestand.'
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
source-git-commit: f87263cde5aa001f78abc368c949ce150feecb91
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Omleiden naar het [!UICONTROL Commerce Admin] -aanmeldingsformulier met de fout &quot;Uw account is tijdelijk uitgeschakeld&quot;

Dit artikel verstrekt de mogelijke oplossingen voor de [!UICONTROL Commerce Admin] login kwestie, waar u terug naar het login formulier met het volgende foutenbericht wordt gericht: *&quot;Uw rekening is tijdelijk gehandicapt&quot;*. De voorgestelde oplossing controleert en verbetert de montages van het admin gebruikersgegevensbestand.

## Betrokken versies en versies:

Alle Adobe Commerce-versies en -versies

## Probleem

<u> Stappen om </u> te reproduceren:

1. Ga naar de pagina **[!UICONTROL Commerce Admin]** .
1. Ga uw geloofsbrieven in en klik **binnen Teken**.

<u> Verwacht resultaat </u>:

U wordt het programma geopend aan [!UICONTROL Commerce Admin].

<u> Werkelijk resultaat </u>:

U wordt teruggeleid naar het aanmeldingsformulier, met het volgende foutbericht weergegeven: *&quot;Uw account is tijdelijk uitgeschakeld. Gelieve te proberen opnieuw later&quot;*.

## Oplossing

1. Maak een back-up van de database.
1. Gebruik een gegevensbestandhulpmiddel zoals [[!DNL phpMyAdmin] ](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin), of toegang manueel OB van de bevellijn. In de `admin_user` gegevensbestandlijst, voor uw admin gebruikersverslag, controleer als `is_active` aan &quot; `1`&quot;wordt geplaatst en `lock_expires` is `NULL`. Stel deze waarden desgewenst opnieuw in.

## Gerelateerde lezing

* [ richt terug naar de login vorm zonder fout, wanneer het proberen om aan [!UICONTROL Commerce Admin] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin) aan te melden
* [ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
