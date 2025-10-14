---
title: Afschrijving van Core Adobe Commerce Payment Integrations
description: Door de PSD van de Richtlijn Betalingsdiensten (zie details over [Richtlijn Betalingsdiensten] (https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html?lang=nl-NL) in onze gebruikershandleiding) en de voortdurende ontwikkeling van veel API's, dreigt een aantal Adobe Commerce Core Payment Integration achterhaald te raken en in de toekomst niet meer aan de beveiligingsvereisten te voldoen. Te dien einde zijn veel belangrijke integratie van de betalingssystemen afgekeurd of zullen deze binnenkort plaatsvinden, en wij bevelen een overgang aan naar de overeenkomstige verlengingen van de Commerce Marketplace. Lees de rest van het onderstaande artikel om recente afwaarderingen van de integratie van betalingen te bekijken. Alle koppelingen **Status** staan in de gebruikershandleiding. **De onderstaande integraties worden allemaal verwijderd uit Adobe Commerce versie 2.4.0 en zijn vervangen door versies van versie 2.3.**
exl-id: c2c4b3b6-409d-466f-a4f3-dfe13ac7f972
feature: Compliance, Integration
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# Afschrijving van Core Adobe Commerce Payment Integrations

Als gevolg van de Richtlijn van de Dienst van de Betaling PSD2 (zie details over [&#x200B; Richtlijn van de Diensten van de Betaling &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html?lang=nl-NL) in onze gebruikersgids) en de voortdurende evolutie van vele APIs, dreigt een aantal de kernbetalingsintegratie van Adobe Commerce achterhaald en niet meer veiligheid volgend in de toekomst te worden. Te dien einde zijn veel belangrijke integratie van de betalingssystemen afgekeurd of zullen deze binnenkort plaatsvinden, en wij bevelen een overgang aan naar de overeenkomstige verlengingen van de Commerce Marketplace. Lees de rest van het onderstaande artikel om recente afwaarderingen van de integratie van betalingen te bekijken. Elk van de **verbindingen van de Status** wordt gevonden in onze gebruikersgids. **de hieronder integratie zal allen uit versie 2.4.0 van Adobe Commerce worden verwijderd en van versies van 2.3 zijn afgekeurd.**

<table style="height: 243px;" width="712">
<tbody>
<tr>
<td style="width: 225.455px;"><strong>Integratie betalingsmethode</strong></td>
<td style="width: 226.364px;"><strong>Status</strong></td>
<td style="width: 226.364px;"><strong>Adobe Commerce 2.X-aanbeveling</strong></td>
</tr>
<tr>
<td style="width: 225.455px;">Worldpay</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=nl-NL#recommended-solutions"> Afgekeurd sinds 2.3.5 </a><br> 2.4.0 - zal volledig worden verwijderd</td>
<td style="width: 226.364px;">Vraag uw betalingsaanbieder welke oplossing zij aanbevelen om aan de PSD2-vereisten te voldoen.</td>
</tr>
<tr>
<td style="width: 225.455px;">Authorize.net</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=nl-NL#recommended-solutions"> Afgekeurd sinds 2.3.4 </a><br> 2.4.0 - zal volledig worden verwijderd</td>
<td style="width: 226.364px;">Gebruik in plaats hiervan de <a href="https://marketplace.magento.com/authorizenet-magento-module-authorizenet.html"> officiële uitbreiding </a> van Commerce Marketplace.</td>
</tr>
<tr>
<td style="width: 225.455px;">Authorize.net (Direct Post)</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=nl-NL#recommended-solutions"> Afgekeurd sinds 2.3.1 </a><br> 2.4.0 - zal volledig worden verwijderd</td>
<td style="width: 226.364px;">Gebruik in plaats hiervan de <a href="https://marketplace.magento.com/authorizenet-magento-module-authorizenet.html"> officiële uitbreiding </a> van Commerce Marketplace.</td>
</tr>
<tr>
<td style="width: 225.455px;">CyberSource</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=nl-NL#recommended-solutions"> Afgekeurd sinds 2.3.3 </a><br> 2.4.0 - zal volledig worden verwijderd</td>
<td style="width: 226.364px;">Gebruik in plaats hiervan de <a href="https://marketplace.magento.com/cybersource-global-payment-management.html"> officiële uitbreiding </a> van Commerce Marketplace.</td>
</tr>
<tr>
<td style="width: 225.455px;">eWay</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=nl-NL#recommended-solutions"> Afgekeurd sinds 2.3.3 </a><br> 2.4.0 - zal volledig worden verwijderd</td>
<td style="width: 226.364px;">Vraag uw betalingsaanbieder welke oplossing zij aanbevelen om aan de PSD2-vereisten te voldoen.</td>
</tr>
</tbody>
</table>

**gelieve nota te nemen, dat de integratie van de de kernbetalingsmethode van PayPal niet zal worden afgekeurd of worden verwijderd en voor alle versies 2.3.x en 2.4.x gesteund.**

## Hoe te om uw betalingen veilig vooruit te houden

Voor alle Adobe Commerce- en Magento Open Source-implementaties die nog steeds gebruikmaken van afgekeurde integratie van betalingen, volgt u de onderstaande aanbevelingen om ervoor te zorgen dat de betalingen van uw klanten veilig zijn, dat betalingen niet worden geweigerd en om de upgrade naar Adobe Commerce 2.4.0 voor te bereiden:

* Installeer en vorm de officiële uitbreiding van de betalingsmethode van [&#x200B; Commerce Marketplace &#x200B;](https://marketplace.magento.com/extensions/payments-security/payment-integration.html?_ga=2.108129217.2105547619.1564067043-238341041.1564067043) zoals die in de lijst hierboven wordt vermeld.
* Maak afgekeurde betaalintegratie in Admin (plaats **Toegelaten** config optie aan *Nr*) onbruikbaar zodat worden zij niet getoond op uw opslag als betalingsopties meer. Zorg ervoor dat alle nieuwe bestellingen worden betaald via de extensie-integratie.
* Aangezien de nieuwe integratie van de Commerce Marketplace geen betalingstransacties zal kunnen verwerken die zijn verricht door een afgekeurde integratie van betalingen, raden wij aan beide betalingsmethoden gedurende een bepaalde periode parallel te gebruiken, maar alleen voor het voltooien van reeds geplaatste transacties en mogelijke terugbetalingen. Om dat te doen, houd vervangen betalingsmethode onbruikbaar, maar verlaat alle configuratievelden bevolkt.
