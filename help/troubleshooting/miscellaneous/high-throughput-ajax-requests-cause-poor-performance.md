---
title: De hoge productie AJAX verzoeken veroorzaken slechte prestaties
description: Dit artikel biedt een oplossing voor prestatieproblemen met Adobe Commerce op locatie of Adobe Commerce op de locatie van de cloudinfrastructuur als gevolg van enkele verzoeken om hoge doorvoer die leiden tot een aanzienlijke serverlading en veel verkeer.
exl-id: 68dfca8a-826c-4476-acaf-a139052b5dcc
feature: Cache
role: Developer
source-git-commit: 3bcdbd0536ec71cb80ffa3afbcd53c4ae385d2e3
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# De hoge productie AJAX verzoeken veroorzaken slechte prestaties

Dit artikel biedt een oplossing voor prestatieproblemen met Adobe Commerce op locatie of Adobe Commerce op de locatie van de cloudinfrastructuur als gevolg van enkele verzoeken om hoge doorvoer die leiden tot een aanzienlijke serverlading en veel verkeer.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur 2.2.x, 2.3.x
* Adobe Commerce op locatie 2.2.x, 2.3.x

>[!NOTE]
>
>Het probleem is opgelost in versie 2.3.4 van zowel Adobe Commerce over cloudinfrastructuur als Adobe Commerce op locatie.

### Probleem

De site heeft te maken met trage prestaties als gevolg van hoge doorvoerverzoeken, zoals essentiële AJAX.

### Oorzaak

De hoge productie AJAX verzoeken omvatten die met betrekking tot de privé inhoud van klanten.

### Oplossing

Er zijn drie oplossingen:

* [ Verbetering aan versie 2.3.4 ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version).
* Verzeker lichtere verzoeken (geheim voorgeheugenverzoeken of ga naar privé inhoud van klanten).
* Verminder het aantal verzoeken.

<u> verzeker lichtere verzoeken (geheim voorgeheugenverzoeken of beweging aan de privé inhoud van klanten) </u>

Als er derde AJAX verzoeken zijn die op elke pagina worden teweeggebracht, probeer om deze verzoeken in het voorgeheugen onder te brengen of hen te bewegen aan de privé inhoud van klanten. De handelaar kan dit doen door ervoor te zorgen dat de douane AJAX verzoeken worden geroepen gebruikend de methodes van HTTP van de GET. Zij zal deze verzoeken snel inwilligen. Als er douaneverzoeken zijn AJAX die niet in het voorgeheugen zouden moeten worden opgeslagen, zouden zij volgens privé-inhoudfunctionaliteit moeten worden verfactored. Voor stappen, verwijs [ Privé Inhoud ](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) in onze ontwikkelaarsdocumentatie.

<u> verminder het aantal verzoeken </u>

* Schakel het hardnekkige winkelwagentje uit, omdat hierdoor het aantal `customer/section/load` -aanvragen kan toenemen. Volg de stappen in [ Persistent het winkelen de wegen van het winkelwagentje ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/paths/config-reference-general) in onze ontwikkelaarsdocumentatie om te zien of wordt de blijvende het winkelwagentje toegelaten.
* Als u inhoud in `sections.xml` moet opnieuw laden of ongeldig maken volg de stappen in [ Privé inhoud: bevestig privé inhoud ](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content) in onze ontwikkelaarsdocumentatie. Zorg ervoor dat u de methode `customerData.reload()` niet rechtstreeks in uw aanpassingen gebruikt.
* Controleer andere POST AJAX verzoeken op dezelfde pagina. Open Google Chrome Developer Tool in Google Chrome browser. Klik op het **lusje van het Netwerk** en dan het **XHR** lusje, en er zal de lijst van alle AJAX verzoeken van de bepaalde pagina zijn. Klik vervolgens op elke aanvraag en in het veld Aanvraagmethode moeten de aanvragen van de GET zijn. Opmerking: Google Chrome wordt als voorbeeld gebruikt en dit is ook mogelijk in andere browsers.
* Controleer de GTM-functionaliteit (Google Tag Manager) die een specifieke AJAX is. De gebruiker kan deze AJAX verwijderen en de aanpassing ervan voorzien van een privéfunctie om het totale aantal aanvragen bij de server te beperken.
* Controleer of de Adobe Commerce Banner is ingeschakeld maar niet wordt gebruikt. U zou [ de output van de Banner van Adobe Commerce kunnen moeten onbruikbaar maken om plaatsprestaties ](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md) te verbeteren.

### Verwante lezing

Voor meer informatie over privé klanteninhoud, herzie [ Privé inhoud ](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) in onze ontwikkelaarsdocumentatie.
