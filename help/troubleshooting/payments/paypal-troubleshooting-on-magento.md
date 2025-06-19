---
title: Problemen met PayPal op Adobe Commerce oplossen
description: Dit artikel biedt oplossingen voor problemen met het verwerken van betalingen via PayPal, met name de Paflow Pro-oplossing. Sommige aanbevelingen in dit artikel lijken misschien voor de hand liggend. Wij vragen u om de het oplossen van problemenopties te proberen die in deze kennisbank worden vermeld en alle informatie in om het even welke kaartjes te omvatten u ingaat. Adobe Commerce of PayPal Support Engineers zullen u vragen deze stappen uit te voeren wanneer u uw problemen diagnosticeert.
exl-id: f0772515-8456-4f08-84b4-aeef44516f2a
feature: Orders, Payments
role: Developer
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# Problemen met PayPal op Adobe Commerce oplossen

Dit artikel biedt oplossingen voor problemen met het verwerken van betalingen via PayPal, met name de Paflow Pro-oplossing. Sommige aanbevelingen in dit artikel lijken misschien voor de hand liggend. Wij vragen u om de het oplossen van problemenopties te proberen die in deze kennisbank worden vermeld en alle informatie in om het even welke kaartjes te omvatten u ingaat. Adobe Commerce of PayPal Support Engineers zullen u vragen deze stappen uit te voeren wanneer u uw problemen diagnosticeert.

## Vaak voorkomende problemen

De meeste problemen met PayPal-betalingen hebben vergelijkbare symptomen: na het opgeven van de betalingskaartgegevens en het voltooien van de afhandeling wordt de betaling niet verwerkt. In plaats daarvan kan er een foutbericht, een betalingsfout of zelfs een lege pagina zijn.

## Verifieer uw geloofsbrieven, cryptsleutels, en vergunningen

Mogelijke problemen: onjuiste accountgegevens (gebruikersnamen, wachtwoorden), ongeldige accounts, verlopen of niet-opgegeven licenties, ongeldige openbare en persoonlijke sleutels en vele andere aspecten. Om die problemen te vinden, zou u ook uw montages van de betalingsconfiguratie kunnen moeten controleren.

## Consistente instellingen toepassen in Adobe Commerce en PayPal

Zorg ervoor dat u dezelfde instellingen hebt toegepast en dezelfde functies hebt ingeschakeld in de instellingen voor Commerce Admin en PayPal-accounts.

### Probleem met voorbeeldinstellingen

Wanneer het toepassen van de Uitdrukkelijke oplossing van de Controle van PayPal, moeten de transacties die op reacties AVS/CSC worden gebaseerd in **Manager PayPal** (de Montages van de Dienst > Opstelling > de Opties van de Veiligheid) en in **Admin van Commerce** ( **Opslag** > Configuratie > **Verkoop** > **de methodes van de Betaling** worden..).
![ magento_paypal_settings_2.4.1.png ](assets/magento_paypal_settings_2.4.1.png)
Voor meer info, zie de documentatie: [ PayPal ](https://www.paypalobjects.com/en_US/vhelp/paypalmanager_help/setup.htm) en [ Adobe Commerce ](/docs/commerce-admin/stores-sales/payments/paypal/paypal-express-checkout.html) in onze gebruikersgids.

## Verwijzingstransacties toestaan

Als uw PayPal-betalingsmethode API&#39;s met factureringsovereenkomsten en referentietransacties omvat, moet u ervoor zorgen dat deze zijn ingeschakeld en correct zijn geconfigureerd in uw instellingen.

### Extra probleemoplossing

Zie de volgende artikelen:

* [ PayPal gateway verworpen verzoek - dubbele factuurkwestie ](https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26838) in onze basis van de steunkennis.
* [ verhogingsidentiteitskaart van de Verandering voor nieuwe opslagentiteit ](/help/how-to/general/change-increment-id-for-a-db-entity-order-invoice-credit-memo-etc-on-particular-store.md) in onze basis van de steunkennis.

## Contact opnemen met de ondersteuningsafdeling om geavanceerde betalingslogboeken te verzamelen

Om gecompliceerde betalingsproblemen op te lossen, kan het Adobe Commerce Support Team u vragen een toegewezen patch toe te passen om geavanceerde betalingsregistratie mogelijk te maken. In dit geval moeten de volgende stappen worden uitgevoerd:

[ leg een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) met de volgende details voor:

* Geef zoveel mogelijk details op voor het probleem.
* Geef een overzicht van de stappen die u hebt geprobeerd vanuit dit artikel, de kennisbasis en andere bronnen. Alle resultaten opnemen.
* Vraag een Advanced Payment Logging patch (referentienummer MDVA-4352) en instructies voor het toepassen van de patch.

Als u de patch voor Geavanceerde betalingsaanmelding ontvangt:

* Breng de pleister aan.
* Verzamel logboeken en maak hen aan uw [ steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) vast.
* Wacht op verdere aanbevelingen van het Adobe Commerce Support Team.
