---
title: Kan gebruiker niet toevoegen aan Adobe Commerce Cloud Project
description: Dit artikel biedt een oplossing als u geen gebruiker kunt toevoegen aan een Adobe Commerce-cloudproject.
exl-id: 59940916-bf92-4e89-a6f9-bca87c54125c
feature: Cloud, Paas
role: Developer
source-git-commit: af74d944553c34da2ac8343695bca49f971bc4e5
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Kan gebruiker niet toevoegen aan Adobe Commerce Cloud Project

Dit artikel verstrekt een oplossing voor wanneer u probeert om een gebruiker aan een wolkenproject toe te voegen, maar het ontbreekt met een fout: *Gebruiker XXX bestaat niet*.

## Betrokken producten en versies

* Adobe Commerce op wolkeninfrastructuur, [ alle gesteunde versies ](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Probleem

Dit artikel biedt een oplossing als u geen gebruiker kunt toevoegen aan een Adobe Commerce-cloudproject.

## Oorzaak

Dit is het verwachte gedrag. De rekening van de gebruiker zou eerst in https://accounts.magento.cloud moeten worden gecreeerd en met hun Adobe SSO voor hen worden verbonden om als gebruiker aan het project worden toegevoegd.

## Oplossing

1. Vraag de gebruiker om zich aan te melden bij zijn account op https://accounts.magento.cloud (ze moeten zich al hebben geregistreerd voor een account op adobe.com onder dat e-mailadres. Het maken/hebben van een account op https://account.adobe.com betekent niet automatisch dat de gebruiker een account heeft op https://accounts.magento.cloud)
Opmerking: als de gebruiker vóór augustus 2022 een account heeft op account.magento.com of accounts.magento.cloud, hebben ze mogelijk geen account bij/op adobe.com, tenzij ze dit account in augustus 2022 of hoger hebben gemaakt. Als de gebruiker een rekening van de Adobe heeft en niet aan login kan, gelieve [ een verzoek van de Steun ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) in https://experienceleague.adobe.com/home#support voorleggen en de details (Reden van de uitgave = Gebruikersbeheer) te verstrekken.
1. De gebruiker moet dan naar https://accounts.magento.cloud gaan.
1. Zodra zij dat hebben gedaan, zou u de gebruiker aan het project moeten kunnen toevoegen. Voor stappen, verwijs naar [ gebruikers toevoegen en toegang ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-users-and-manage-access) in onze Commerce op de Gids van de Infrastructuur van de Wolk beheren.

## Gerelateerde lezing:

* [ beheer gebruikerstoegang ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) in onze Commerce op de Gids van de Infrastructuur van de Wolk.
* [ Onbekwaam aan login aan de steun van Adobe Commerce of wolkenrekening ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html)
