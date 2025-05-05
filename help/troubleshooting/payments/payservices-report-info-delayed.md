---
title: Vertraagde rapportgegevens van betalingsservices
description: In dit artikel wordt uitgelegd waarom de rapportage van gegevens in Betalingsdiensten kan worden vertraagd.
exl-id: 2f3249d1-be12-45bc-aa73-bef9766509ae
feature: Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Vertraagde rapportgegevens van betalingsservices

In dit artikel wordt uitgelegd waarom de rapportage van gegevens in Betalingsdiensten kan worden vertraagd.

## Betrokken producten en versies

* [ de Diensten van de Betaling ](https://marketplace.magento.com/magento-payment-services.html) is nu compatibel met versies 2.4.0 van Adobe Commerce aan 2.4.4.

## Probleem

Betalingsdiensten die gegevens rapporteren, voor Betalingsstatusrapporten voor betaling en bestelling, kunnen niet meteen synchroniseren.

Nadat u een bestelling hebt gefactureerd (vastgelegd) of een creditnota voor een bestelling hebt uitgegeven, bijvoorbeeld, is de status van de bestelling mogelijk niet onmiddellijk beschikbaar.

<u> Stappen om </u> te reproduceren:

Vereisten: een bestelling wordt geplaatst met behulp van de functionaliteit Betalingsservices.

1. Een orde wordt [ gefactureerd ](https://experienceleague.adobe.com/nl/docs/commerce-admin/stores-sales/order-management/invoices#create-an-invoice) (of [ geannuleerd ](https://experienceleague.adobe.com/nl/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order) of [ die via creditmemo ](https://experienceleague.adobe.com/nl/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memos) worden teruggegeven) in [ Admin ](https://experienceleague.adobe.com/nl/docs/commerce-admin/start/admin/admin).
1. Navigeer naar het rapport Betalingsstatus bestellen voor informatie over die bestelling.
1. De status wordt weergegeven als `AUTHORIZED` . Dit is de status van de bestelling voorafgaand aan het factureren of een andere bestelling.

   Commerce heeft geen gegevens gesynchroniseerd en deze naar Payment Services verzonden, zodat de nieuwe status van de bestelling nog niet in het rapport wordt herkend.

>[!NOTE]
>
>Dit is slechts één algemeen geval van gebruik. Er kunnen andere gebruiksgevallen zijn wanneer een [ ordeactie ](https://experienceleague.adobe.com/nl/docs/commerce-admin/stores-sales/order-management/orders/orders#actions) voorkomt en het gegeven niet onmiddellijk beschikbaar in het toepasselijke rapport is.

<u> Verwacht resultaat </u>:
Rapportgegevens worden direct ingevuld nadat een handeling op een bestelling is uitgevoerd.

<u> Werkelijk resultaat </u>:
Er kan een vertraging optreden in zichtbare rapportgegevens voor zojuist voltooide bestelacties. Uitbetalingsrapporten kunnen een vertraging van 24 tot 48 uur hebben. Betalingsstatusrapporten van bestellingen kunnen een paar uur vertraging oplopen.

## Oorzaak

Er zijn twee factoren die deze vertraging in de zichtbare gegevens in de Admin beïnvloeden:

* Hoe vaak u verkiest om (de uitvoer en voorhoudt) gegevens van Commerce, via [ configuratie in Admin ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/configure-admin.html?lang=nl-NL) te synchroniseren.
* Tijdschema waarin PayPal rapportgegevens publiceert.

## Oplossing

Voor de betalingsstatusrapporten van bestellingen:

1. Navigeer aan **Verkoop** > **de Diensten van de Betaling**.
1. Klik **de betalingsstatus van de Orde** om de lijst van de statusrapporten van de ordebetaling te bekijken.
1. Drijf resync door het **kracht te klikken resync** pictogram in de hoogste juiste hoek van de rapportlijst.
1. De laatste bijgewerkte tijdstempelwijziging en nieuwe transacties die in de rapporttabel zijn geladen, worden weergegeven.

Voor PayPal-uitbetalingsrapporten is het verwachte resultaat een vertraging van 24 tot 48 uur vanwege de afhankelijkheid van het tijdpad voor het publiceren van gegevens van PayPal.
