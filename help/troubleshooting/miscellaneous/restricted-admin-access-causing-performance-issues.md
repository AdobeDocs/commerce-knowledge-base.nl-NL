---
title: Beperkte toegang tot beheerder leidt tot prestatieproblemen
description: Dit artikel biedt oplossingen voor situaties waarin de prestaties negatief worden beïnvloed door het gebruik van [Admin-rollen met rolbereik beperkt door website](https://docs.magento.com/m2/ee/user_guide/system/permissions-user-roles.html#step-2assign-resources) in onze gebruikershandleiding.
exl-id: da168d6b-9cda-41e2-aa3c-f3f0dccc803d
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Beperkte toegang tot beheerder leidt tot prestatieproblemen

Dit artikel biedt oplossingen voor situaties waarin de prestaties negatief worden beïnvloed door het gebruik [Beheerdersrollen met rolbereik beperkt door website](https://docs.magento.com/m2/ee/user_guide/system/permissions-user-roles.html#step-2assign-resources) in onze gebruikershandleiding.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.2.x, 2.3.x
* Adobe Commerce op cloud-infrastructuur 2.2.x, 2.3.x

## Probleem

Wanneer een Admin-gebruiker, met het rolbereik beperkt door de website, bewerkingen uitvoert in het beheerpaneel (zoals aanmelden, producten opslaan enzovoort), bouwt Adobe Commerce de opgeslagen cache opnieuw op. Het opnieuw samenstellen van het geheime voorgeheugen beïnvloedt prestaties negatief en kan tot een plaatsuitbarsting, vooral tijdens zaken en/of hoog-verkeersuren leiden.

Het probleem is opgelost in Adobe Commerce 2.2.10 en 2.3.3.

## Oplossing

Hieronder vindt u opties om dit probleem te voorkomen:

* Voer een upgrade uit van de Adobe Commerce-toepassingsversie naar 2.2.10 of 2.3.3. (zie voor instructies de [Adobe Commerce upgraden op versie van cloudinfrastructuur](https://devdocs.magento.com/guides/v2.3/cloud/project/project-upgrade.html) in onze ontwikkelaarsdocumentatie).
* Beperk indien mogelijk het bereik van de beheerdersrol niet per website.
* [Een ondersteuningsticket voor Magento&#39;s verzenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), om een pleister aan te vragen, als deze beschikbaar is.

## Gerelateerde lezing

* [Gebruikersrollen](https://docs.magento.com/m2/ee/user_guide/system/permissions-user-roles.html) in onze gebruikershandleiding.
