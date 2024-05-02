---
title: Kan gebruiker niet toevoegen aan Adobe Commerce Cloud Project
description: Dit artikel biedt een oplossing als u geen gebruiker kunt toevoegen aan een Adobe Commerce-cloudproject.
exl-id: 59940916-bf92-4e89-a6f9-bca87c54125c
feature: Cloud, Paas
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Kan gebruiker niet toevoegen aan Adobe Commerce Cloud Project

Dit artikel biedt een oplossing wanneer u een gebruiker aan een wolkenproject probeert toe te voegen, maar het ontbreekt met een fout: *Gebruiker XXX bestaat niet*.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, [alle ondersteunde versies](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Probleem

Dit artikel biedt een oplossing als u geen gebruiker kunt toevoegen aan een Adobe Commerce-cloudproject.

## Oorzaak

Dit is het verwachte gedrag. De rekening van de gebruiker zou eerst in https://accounts.magento.cloud moeten worden gecreeerd en met hun Adobe SSO voor hen worden verbonden om als gebruiker aan het project worden toegevoegd.

## Oplossing

1. Vraag de gebruiker om zich aan te melden bij zijn account op https://accounts.magento.cloud (ze moeten zich al hebben geregistreerd voor een account op adobe.com onder dat e-mailadres. Het maken/hebben van een account op https://account.adobe.com betekent niet automatisch dat de gebruiker een account op https://accounts.magento.cloud) heeft. Opmerking: als de gebruiker vóór augustus 2022 een account op account.magento.com of accounts.magento.cloud had, hebben ze mogelijk geen account met of op adobe.com, tenzij ze dit account in augustus 2022 of hoger hadden gemaakt. Als de gebruiker een Adobe-account heeft en zich niet kan aanmelden, stuurt u een e-mail naar [Grp-Magento-HelpCenterLoginIssues@adobe.com](mailto:Grp-Magento-HelpCenterLoginIssues@adobe.com) met de details.
1. De gebruiker moet dan naar https://accounts.magento.cloud gaan.
1. Zodra zij dat hebben gedaan, zou u de gebruiker aan het project moeten kunnen toevoegen. Raadpleeg voor stappen [Gebruikers toevoegen en toegang beheren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-users-and-manage-access) in onze Commerce on Cloud Infrastructure Guide.

## Gerelateerde lezing:

* [Gebruikerstoegang beheren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) in onze Commerce on Cloud Infrastructure Guide.
* [Kan niet aanmelden bij Adobe Commerce-ondersteuning of cloudaccount](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html)
