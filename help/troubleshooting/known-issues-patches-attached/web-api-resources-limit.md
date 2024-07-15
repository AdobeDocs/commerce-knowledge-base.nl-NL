---
title: Web API kan aanvragen met meer dan 20 items in matrix niet verwerken
description: Dit artikel biedt een oplossing voor het probleem waarbij Web API geen bericht kan verwerken dat meer dan 20 items in de array voor Adobe Commerce 2.4.3 bevat.
exl-id: 7e6b3fe8-3133-4773-afa7-fbfdd98ecde9
feature: REST
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Web API kan aanvragen met meer dan 20 items in matrix niet verwerken

Dit artikel biedt een oplossing voor het probleem waarbij Web API geen bericht kan verwerken dat meer dan 20 items in de array voor Adobe Commerce 2.4.3 bevat.

## Betrokken producten en versies:

* Adobe Commerce (alle implementatiemethoden) 2.4.3 en 2.3.7-p1
* Magento Open Sourcen 2.4.3 en 2.3.7-p1

## Probleem

Web API kan het bericht (bijvoorbeeld Stock Update) niet verwerken dat meer dan 20 items in een array bevat.

## Oorzaak

In Adobe Commerce 2.4.3 werd de ingebouwde snelheidsbeperking toegevoegd aan Magento APIs om ontkenning-van-dienst (Dos) aanvallen te verhinderen.

Standaard is de volgende beperking van de ingebouwde API-snelheid beschikbaar:

* REST-verzoeken die inputs bevatten die een lijst van entiteiten vertegenwoordigen, zijn beperkt tot een standaardmaximum van 20 entiteiten
* REST- en GraphQL-query&#39;s die gepagineerde resultaten toestaan, zijn beperkt tot een standaardmaximum van 300 items per pagina

## Oplossing

Als u de invoerbeperkingen voor de REST API-aanvraag wilt uitschakelen, past u een van de volgende patches toe (afhankelijk van uw versie):

* [MC-43048__set_rate_limits__2.3.7-p1.patch.zip](assets/MC-43048__set_rate_limits__2.3.7-p1.patch.zip)
* [MC-43048__set_rate_limits__2.4.3.patch.zip](assets/MC-43048__set_rate_limits__2.4.3.patch.zip)

### Compatibele Adobe Commerce-versies

De patches zijn gemaakt voor:

* Adobe Commerce op cloudinfrastructuur 2.4.3 en 2.3.7-p1
* Adobe Commerce op locatie 2.4.3 en 2.3.7-p1

De patches zijn niet compatibel met andere Adobe Commerce-versies.

### Hoe de pleister aanbrengen

Pak het gedownloade `.zip` dossier uit en pas het flard toe zoals die in [ wordt beschreven hoe te om een composerflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) wordt verstrekt.

>[!WARNING]
>
>Als u vermoedt dat uw winkel een DoS-aanval ondervindt, raadt de Adobe u aan de standaardinvoerbeperkingen tot een lagere waarde te verlagen om het aantal bronnen dat kan worden aangevraagd, te beperken.  U kunt de standaardgrenzen programmatically aanpassen gebruikend [ argumenten van de klassenaannemer ](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html)
>zoals die in onze ontwikkelaarsdocumentatie wordt beschreven: [ API veiligheid > het Beperken van het Tarief > Maximale parameterinput ](https://devdocs.magento.com/guides/v2.4/get-started/api-security.html#rate-limiting).

## Gerelateerde lezing

[ API veiligheid > het Beperken van het Tarief ](https://devdocs.magento.com/guides/v2.4/get-started/api-security.html#rate-limiting) in onze ontwikkelaarsdocumentatie.
