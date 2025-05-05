---
title: 'FOUT: Opwarmen is mislukt in Adobe Commerce op cloudinfrastructuur'
description: 'Dit artikel biedt een oplossing voor het opwarmen van de paginacache en het mislukken van een fout:'
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# FOUT: Opwarmen is mislukt in Adobe Commerce op cloudinfrastructuur

Dit artikel biedt een oplossing voor het opwarmen van de paginacache en het mislukken van een fout:

*FOUT: Opwarmen is mislukt:`<website link>`*

## Betrokken producten en versies

* Adobe Commerce op wolkeninfrastructuur, alle [ gesteunde versies ](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Probleem

Opwarmen van cache mislukt.

<u> Stappen om </u> te reproduceren:

Opwarmbewerkingen in cache starten.

<u> Verwacht resultaat </u>:

Pagina&#39;s of de hele site wordt geladen.

<u> Werkelijk resultaat </u>:

De site is niet beschikbaar of de responstijd is te hoog. *FOUT: Opwarmen is mislukt:`<website link>`*

## Oorzaak

Opwarmen van cache werkt niet met ingeschakelde HTTP-toegangscontrole.

## Oplossing

Zorg ervoor dat u geen toegelaten toegangsbeheer hebt: ga naar de specifieke tak/het milieu en klik op het **pictogram van Montages**, en controleer het **de toegangsbeheer van HTTP** plaatsen - geheime voorgeheugen warm-up kan niet in dit scenario voorkomen, en toegangsbeheer moet worden onbruikbaar gemaakt.

## Gerelateerde lezing

* [ de Gids van de Gebruiker van Adobe Commerce > het Geheime voorgeheugen van de Volledige Pagina ](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/tools/cache-management#full-page-caching) in onze gebruikersgids.
* [ Geheime voorgeheugen opwarmt en plaats niet beschikbaar op Adobe Commerce ](/help/troubleshooting/miscellaneous/cache-warming-up-and-site-unavailable-on-magento.md) in onze basis van de steunkennis.
