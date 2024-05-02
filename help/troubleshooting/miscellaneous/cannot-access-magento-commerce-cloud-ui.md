---
title: Kan Adobe Commerce niet openen op interface van cloudinfrasinfrastructuur
description: Dit artikel biedt oplossingen voor het probleem waarbij u zich niet kunt aanmelden bij uw Adobe Commerce op de interface van de cloudinfrastructuur en de fout "403" krijgt.
exl-id: 948e4acd-abd6-4562-b9c0-771a977188ba
feature: Cloud, Paas
role: Developer
source-git-commit: 3d3d2da45d164efbbbaf8c878967caf83f845a59
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Kan Adobe Commerce niet openen op interface van cloudinfrasinfrastructuur

Dit artikel biedt oplossingen voor het probleem waarbij u zich niet kunt aanmelden bij uw Adobe Commerce op de interface van de cloud-infrastructuur en de *403-fout*.

## Probleem

Wanneer u zich voor het eerst aanmeldt bij de gebruikersinterface van uw Adobe Commerce-cloudinfrastructuur, krijgt u een *403: Toegang tot omgeving geweigerd* fout. Deze fout kan optreden omdat het gaan naar de wolk URL voor de eerste keer de hoofdtak laadt, en u zou geen toegang tot die tak kunnen hebben.

## Oplossing

Als u een fout van 403 krijgt wanneer u tot URL voor het eerst toegang hebt, zorg ervoor u een rol in de hoofdtak hebt.

1. С contact op met de eigenaar van de licentie of een supergebruiker voor het project en zorg ervoor dat deze als **gebruiker op milieuniveau**, ook beschreven in [Cloud projects > Manage users from the Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-from-the-cloud-console) in onze ontwikkelaarsdocumentatie.

   Als u slechts een toepasselijke rol in een specifieke tak hebt, dan zou u naar URL voor die tak, bijvoorbeeld, moeten gaan
   `https://console.adobecommerce.com/<owner-name>/<project-id>/<branch-name>`

   De volgende keer dat u de hoofd-URL opent, wordt standaard de laatste omgeving gebruikt die u hebt bezocht.

1. Als u zich nog steeds niet kunt aanmelden, neemt с contact op met de eigenaar van de licentie of een supergebruiker van het project en zorgt u ervoor dat deze als een **gebruiker op projectniveau**, zoals beschreven in [Cloud projects > Add a user to the project](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-a-user-to-the-project) in onze ontwikkelaarsdocumentatie.
1. Als de fout blijft bestaan, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
