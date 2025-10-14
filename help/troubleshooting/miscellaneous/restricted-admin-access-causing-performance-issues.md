---
title: Beperkte toegang tot beheerder leidt tot prestatieproblemen
description: Dit artikel biedt oplossingen voor situaties waarin de prestaties negatief worden beïnvloed door het gebruik van [Admin-rollen met rolbereik beperkt door website](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/user-accounts/permissions-user-roles#step-2assign-resources) in onze gebruikershandleiding.
exl-id: da168d6b-9cda-41e2-aa3c-f3f0dccc803d
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Beperkte toegang tot beheerder leidt tot prestatieproblemen

Dit artikel verstrekt oplossingen voor wanneer de prestaties negatief worden beïnvloed door [&#x200B; rollen Admin met rolwerkingsgebied te gebruiken dat door website &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/user-accounts/permissions-user-roles#step-2assign-resources) in onze gebruikersgids wordt beperkt.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.2.x, 2.3.x
* Adobe Commerce op cloud-infrastructuur 2.2.x, 2.3.x

## Probleem

Wanneer een Admin-gebruiker, met het rolbereik beperkt door de website, bewerkingen uitvoert in het beheerpaneel (zoals aanmelden, producten opslaan enzovoort), bouwt Adobe Commerce de opgeslagen cache opnieuw op. Het opnieuw samenstellen van het geheime voorgeheugen beïnvloedt prestaties negatief en kan tot een plaatsuitbarsting, vooral tijdens zaken en/of hoog-verkeersuren leiden.

Het probleem is opgelost in Adobe Commerce 2.2.10 en 2.3.3.

## Oplossing

Hieronder vindt u opties om dit probleem te voorkomen:

* Voer een upgrade uit van de Adobe Commerce-toepassingsversie naar 2.2.10 of 2.3.3. (voor instructies, zie de [&#x200B; Verbetering Adobe Commerce op versie van de wolkeninfrastructuur &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) in onze ontwikkelaarsdocumentatie).
* Beperk indien mogelijk het bereik van de beheerdersrol niet per website.
* [&#x200B; leg een kaartje van de Steun van het Magento &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voor, om een flard te verzoeken, als het beschikbaar is.

## Gerelateerde lezing

* [&#x200B; de rollen van de Gebruiker &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/user-accounts/permissions-user-roles) in onze gebruikersgids.
