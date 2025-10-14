---
title: AJAX-verzoeken met hoge doorvoer leveren slechte prestaties op
description: Dit artikel biedt een oplossing voor prestatieproblemen met Adobe Commerce op locatie of Adobe Commerce op de locatie van de cloudinfrastructuur als gevolg van enkele verzoeken om hoge doorvoer die leiden tot een aanzienlijke serverlading en veel verkeer.
exl-id: 68dfca8a-826c-4476-acaf-a139052b5dcc
feature: Cache
role: Developer
source-git-commit: b6e44e106dcc546949459a79c0f2e49b87e1d376
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# AJAX-verzoeken met hoge doorvoer leveren slechte prestaties op

Dit artikel biedt een oplossing voor prestatieproblemen met Adobe Commerce op locatie of Adobe Commerce op de locatie van de cloudinfrastructuur als gevolg van enkele verzoeken om hoge doorvoer die leiden tot een aanzienlijke serverlading en veel verkeer.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur 2.2.x, 2.3.x
* Adobe Commerce op locatie 2.2.x, 2.3.x

>[!NOTE]
>
>Het probleem is opgelost in versie 2.3.4 van zowel Adobe Commerce over cloudinfrastructuur als Adobe Commerce op locatie.

### Probleem

De site heeft te maken met trage prestaties als gevolg van hoge doorvoerverzoeken, zoals kritieke AJAX-verzoeken.

### Oorzaak

De hoge productie AJAX verzoeken omvatten die met betrekking tot de privé inhoud van klanten.

### Oplossing

Er zijn drie oplossingen:

* [&#x200B; Verbetering aan versie 2.3.4 &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version).
* Verzeker lichtere verzoeken (geheim voorgeheugenverzoeken of ga naar privé inhoud van klanten).
* Verminder het aantal verzoeken.

<u> verzeker lichtere verzoeken (geheim voorgeheugenverzoeken of beweging aan de privé inhoud van klanten) </u>

Als er AJAX-verzoeken van derden zijn die op elke pagina worden geactiveerd, probeert u deze aanvragen in cache te plaatsen of naar de persoonlijke inhoud van de klant te verplaatsen. De handelaar kan dit doen door ervoor te zorgen dat de douaneverzoeken van AJAX gebruikend de methodes van HTTP van GET worden geroepen. Zij zal deze verzoeken snel inwilligen. Als er de verzoeken van douaneAJAX zijn die niet in het voorgeheugen zouden moeten worden opgeslagen, zouden zij volgens privé-inhoudfunctionaliteit moeten worden verfactored. Voor stappen, verwijs [&#x200B; Privé Inhoud &#x200B;](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) in onze ontwikkelaarsdocumentatie.

<u> verminder het aantal verzoeken </u>

* Schakel het hardnekkige winkelwagentje uit, omdat hierdoor het aantal `customer/section/load` -aanvragen kan toenemen. Volg de stappen in [&#x200B; Persistent het winkelen de wegen van het winkelwagentje &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/paths/config-reference-general) in onze ontwikkelaarsdocumentatie om te zien of wordt de blijvende het winkelwagentje toegelaten.
* Als u inhoud in `sections.xml` moet opnieuw laden of ongeldig maken volg de stappen in [&#x200B; Privé inhoud: bevestig privé inhoud &#x200B;](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content) in onze ontwikkelaarsdocumentatie. Zorg ervoor dat u de methode `customerData.reload()` niet rechtstreeks in uw aanpassingen gebruikt.
* Controleer andere POST AJAX-aanvragen op dezelfde pagina. Open Google Chrome Developer Tool in Google Chrome browser. Klik op het **lusje van het Netwerk** en dan het **XHR** lusje, en er zal de lijst van alle verzoeken van AJAX van de bepaalde pagina zijn. Klik vervolgens op elke aanvraag en in het veld Aanvraagmethode moeten de GET-aanvragen worden vermeld. Opmerking: Google Chrome wordt als voorbeeld gebruikt en dit is ook mogelijk in andere browsers.
* Controleer de GTM-functionaliteit (Google Tag Manager) die een specifieke AJAX-aanvraag is. De gebruiker kan deze AJAX verwijderen en de aanpassing ervan voorzien van een privéfunctie om het totale aantal aanvragen bij de server te beperken.
* Controleer of de Adobe Commerce Banner is ingeschakeld maar niet wordt gebruikt. U zou [&#x200B; de output van de Banner van Adobe Commerce kunnen moeten onbruikbaar maken om plaatsprestaties &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26909) te verbeteren.

### Verwante lezing

Voor meer informatie over privé klanteninhoud, herzie [&#x200B; Privé inhoud &#x200B;](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) in onze ontwikkelaarsdocumentatie.
