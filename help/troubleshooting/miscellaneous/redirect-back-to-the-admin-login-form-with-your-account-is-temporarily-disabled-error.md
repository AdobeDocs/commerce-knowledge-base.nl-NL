---
title: Omleiden naar het aanmeldingsformulier voor Commerce Admin met de fout "Uw account is tijdelijk uitgeschakeld"
description: 'Dit artikel biedt de mogelijke oplossingen voor het aanmeldingsprobleem van Commerce Admin, waarbij u weer naar het aanmeldingsformulier wordt omgeleid met het volgende foutbericht: *"Uw account is tijdelijk uitgeschakeld"*. De voorgestelde oplossing controleert en verbetert de montages van het admin gebruikersgegevensbestand.'
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Omleiden naar het aanmeldingsformulier voor Commerce Admin met de fout &quot;Uw account is tijdelijk uitgeschakeld&quot;

Dit artikel bevat de mogelijke oplossingen voor het aanmeldingsprobleem van Commerce Admin, waarbij u met het volgende foutbericht terugkeert naar het aanmeldingsformulier: *&quot;Uw account is tijdelijk uitgeschakeld.&quot;*. De voorgestelde oplossing controleert en verbetert de montages van het admin gebruikersgegevensbestand.

## Betrokken versies en versies:

Alle Adobe Commerce-versies en -versies

## Probleem

<u>Stappen om te reproduceren</u>:

1. Ga naar de pagina Commerce Admin.
1. Voer uw referenties in en klik op Aanmelden.

<u>Verwacht resultaat</u>:

U wordt aangemeld bij de Commerce Admin.

<u>Werkelijk resultaat</u>:

U wordt opnieuw omgeleid naar het aanmeldingsformulier, met het volgende foutbericht weergegeven: *&quot;Uw account is tijdelijk uitgeschakeld. Probeer het later opnieuw.&quot;*.

## Oplossing

1. Maak een back-up van de database.
1. Een databasegereedschap gebruiken, zoals [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin)of opent u de database handmatig via de opdrachtregel. In de `admin_user` databasetabel, voor de gebruikersrecord van uw beheerder, controleert u of `is_active` is ingesteld op &quot;`1`&quot; en `lock_expires` is `NULL`. Stel deze waarden desgewenst opnieuw in.

## Gerelateerde lezing in onze kennisbasis voor support

* [Omleiden naar het aanmeldingsformulier zonder fout wanneer u zich probeert aan te melden bij de Commerce Admin](/help/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin.md)
