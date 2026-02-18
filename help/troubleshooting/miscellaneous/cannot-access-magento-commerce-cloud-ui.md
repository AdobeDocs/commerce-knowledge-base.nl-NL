---
title: Kan Adobe Commerce niet openen op interface van cloudinfrasinfrastructuur
description: Dit artikel biedt oplossingen voor het probleem waarbij u zich niet kunt aanmelden bij uw Adobe Commerce op de interface van de cloudinfrastructuur en de fout "403" krijgt.
exl-id: 948e4acd-abd6-4562-b9c0-771a977188ba
feature: Cloud, Paas
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Kan Adobe Commerce niet openen op interface van cloudinfrasinfrastructuur

Dit artikel verstrekt oplossingen voor de kwestie waar u niet login aan uw Adobe Commerce op de interface van de wolkeninfrastructuur kunt en de *403 fout* krijgt.

## Probleem

Wanneer het proberen om aan uw Adobe Commerce op de interface van de wolkeninfrastructuur voor het eerst te registreren, krijgt u a *403: Afgewezen van de Toegang van het Milieu* fout. Deze fout kan optreden omdat het gaan naar de wolk URL voor de eerste keer de hoofdtak laadt, en u zou geen toegang tot die tak kunnen hebben.

## Oplossing

Als u een fout van 403 krijgt wanneer u tot URL voor het eerst toegang hebt, zorg ervoor u een rol in de hoofdtak hebt.

1. С de vergunningseigenaar of een super gebruiker op het project in werking te stellen en ervoor te zorgen zij toegang tot u als **milieu-vlakke gebruiker** verstrekten, ook die in [&#x200B; de projecten van de Wolk > gebruikers van de Console van de Wolk &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-from-the-cloud-console) in onze ontwikkelaarsdocumentatie wordt beschreven.

   Als u slechts een toepasselijke rol in een specifieke tak hebt, dan zou u naar URL voor die tak, bijvoorbeeld, moeten gaan
   `https://console.adobecommerce.com/<owner-name>/<project-id>/<branch-name>`

   De volgende keer dat u de hoofd-URL opent, wordt standaard de laatste omgeving gebruikt die u hebt bezocht.

1. Als u nog niet login kunt, с de vergunningseigenaar of een super gebruiker op het project in werking stellen en ervoor zorgen zij toegang voor u als a **project-vlakke gebruiker** verstrekten, zoals die in [&#x200B; de projecten van de Wolk > een gebruiker aan het project &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-a-user-to-the-project) in onze ontwikkelaarsdocumentatie wordt beschreven.
1. Als de fout voortduurt, [&#x200B; voorlegt een steunkaartje &#x200B;](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket).
