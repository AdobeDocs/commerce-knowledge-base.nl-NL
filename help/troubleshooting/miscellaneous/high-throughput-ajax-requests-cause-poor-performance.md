---
title: De hoge productie AJAX verzoeken veroorzaken slechte prestaties
description: Dit artikel biedt een oplossing voor prestatieproblemen met Adobe Commerce op locatie of Adobe Commerce op de locatie van de cloudinfrastructuur als gevolg van enkele verzoeken om hoge doorvoer die leiden tot een aanzienlijke serverlading en veel verkeer.
exl-id: 68dfca8a-826c-4476-acaf-a139052b5dcc
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '499'
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

* [Upgrade naar versie 2.3.4](https://devdocs.magento.com/cloud/project/project-upgrade.html). Als dit momenteel niet mogelijk is, [de patch installeren om het probleem op te lossen](/help/troubleshooting/known-issues-patches-attached/performance-issues-caused-by-excessive-ajax-requests.md).
* Verzeker lichtere verzoeken (geheim voorgeheugenverzoeken of ga naar privé inhoud van klanten).
* Verminder het aantal verzoeken.

<u>Lichtere verzoeken verzekeren (cacheverzoeken of overschakelen naar persoonlijke inhoud van klanten)</u>

Als er derde AJAX verzoeken zijn die op elke pagina worden teweeggebracht, probeer om deze verzoeken in het voorgeheugen onder te brengen of hen te bewegen aan de privé inhoud van klanten. De handelaar kan dit doen door ervoor te zorgen dat de douane AJAX verzoeken worden geroepen gebruikend de methodes van HTTP van de GET. Zij zal deze verzoeken snel inwilligen. Als er douaneverzoeken zijn AJAX die niet in het voorgeheugen zouden moeten worden opgeslagen, zouden zij volgens privé-inhoudfunctionaliteit moeten worden verfactored. Raadpleeg voor stappen [Persoonlijke inhoud](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html) in onze ontwikkelaarsdocumentatie.

<u>Het aantal aanvragen verminderen</u>

* De hardnekkige winkelwagentje uitschakelen, omdat hierdoor het aantal `customer/section/load` verzoeken. Voer de stappen uit in [Blijvende winkelwagentjes](https://devdocs.magento.com/guides/v2.3/config-guide/prod/config-reference-most.html#persistent-shopping-cart-paths) in onze documentatie voor ontwikkelaars om te zien of is persistente winkelwagentjes mogelijk .
* Als u inhoud opnieuw moet laden of ongeldig moet maken in `sections.xml` Volg de stappen in [Persoonlijke inhoud: persoonlijke inhoud ongeldig maken](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html#invalidate-private-content) in onze ontwikkelaarsdocumentatie. Zorg ervoor dat u de opdracht `customerData.reload()` rechtstreeks in uw aanpassingen.
* Controleer andere POST AJAX verzoeken op dezelfde pagina. Open Google Chrome-ontwikkelaarsgereedschap in de Google Chrome-browser. Klik op de knop **Netwerk** en vervolgens de **XHR** en er is een lijst met alle AJAX aanvragen van de desbetreffende pagina. Klik vervolgens op elke aanvraag en in het veld Aanvraagmethode moeten de aanvragen van de GET zijn. Opmerking: Google Chrome wordt als voorbeeld gebruikt en dit is ook mogelijk in andere browsers.
* Controleer de GTM-functionaliteit (Google Tag Manager) die een specifieke AJAX is. De gebruiker kan deze AJAX verwijderen en de aanpassing ervan voorzien van een privéfunctie om het totale aantal aanvragen bij de server te beperken.
* Controleer of de Adobe Commerce Banner is ingeschakeld maar niet wordt gebruikt. Mogelijk moet u [Uitvoer van Adobe Commerce Banner uitschakelen om de prestaties van de site te verbeteren](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md).

### Verwante lezing

Voor meer informatie over inhoud van privéklanten raadpleegt u [Persoonlijke inhoud](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=ajax%20requests) in onze ontwikkelaarsdocumentatie.
