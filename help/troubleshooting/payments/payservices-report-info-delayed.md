---
title: Vertraagde rapportgegevens van betalingsservices
description: In dit artikel wordt uitgelegd waarom de rapportage van gegevens in Betalingsdiensten kan worden vertraagd.
exl-id: 2f3249d1-be12-45bc-aa73-bef9766509ae
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Vertraagde rapportgegevens van betalingsservices

In dit artikel wordt uitgelegd waarom de rapportage van gegevens in Betalingsdiensten kan worden vertraagd.

## Betrokken producten en versies

* [Betalingsdiensten](https://marketplace.magento.com/magento-payment-services.html) is nu compatibel met Adobe Commerce-versies 2.4.0 tot en met 2.4.4.

## Probleem

Betalingsdiensten die gegevens rapporteren, voor Betalingsstatusrapporten voor betaling en bestelling, kunnen niet meteen synchroniseren.

Nadat u een bestelling hebt gefactureerd (vastgelegd) of een creditnota voor een bestelling hebt uitgegeven, bijvoorbeeld, is de status van de bestelling mogelijk niet onmiddellijk beschikbaar.

<u>Stappen om te reproduceren</u>:

Vereisten: een bestelling wordt geplaatst met behulp van de functionaliteit Betalingsservices.

1. Een bestelling is [gefactureerd](https://docs.magento.com/user-guide/sales/invoice-create.html) (of [geannuleerd](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order) of [terugbetaald via creditmemo](https://docs.magento.com/user-guide/sales/credit-memos.html)) in de [Beheerder](https://docs.magento.com/user-guide/stores/admin.html).
1. Navigeer naar het rapport Betalingsstatus bestellen voor informatie over die bestelling.
1. De status wordt weergegeven als `AUTHORIZED`, dat wil zeggen de status van de bestelling voorafgaand aan de facturering of andere bestelling.

   Commerce heeft geen gegevens gesynchroniseerd en deze naar Payment Services verzonden, zodat de nieuwe status van de bestelling nog niet in het rapport wordt herkend.

>[!NOTE]
>
>Dit is slechts één algemeen geval van gebruik. Er kunnen andere gevallen van gebruik zijn wanneer een [Handeling order](https://docs.magento.com/user-guide/sales/order-actions.html) voorkomt en de gegevens niet onmiddellijk beschikbaar zijn in het toepasselijke rapport.

<u>Verwacht resultaat</u>: Rapportgegevens worden direct gevuld nadat een handeling op een bestelling is uitgevoerd.

<u>Werkelijk resultaat</u>: Er kan een vertraging optreden in zichtbare rapportgegevens voor zojuist voltooide bestelacties. Uitbetalingsrapporten kunnen een vertraging van 24 tot 48 uur hebben. Betalingsstatusrapporten van bestellingen kunnen een paar uur vertraging oplopen.

## Oorzaak

Er zijn twee factoren die deze vertraging in de zichtbare gegevens in de Admin beïnvloeden:

* Hoe vaak u ervoor kiest om gegevens uit Commerce te synchroniseren (exporteren en behouden), via [configuratie in de beheerder](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/configure-admin.html).
* Tijdschema waarin PayPal rapportgegevens publiceert.

## Oplossing

Voor de betalingsstatusrapporten van bestellingen:

1. Navigeren naar **Verkoop** > **Betalingsdiensten**.
1. Klikken **Betalingsstatus bestellen** om de tabel met betalingsstatusrapporten voor bestellingen te bekijken.
1. Opnieuw synchroniseren forceren door op de knop **forceren resync** in de rechterbovenhoek van de rapportentabel.
1. De laatste bijgewerkte tijdstempelwijziging en nieuwe transacties die in de rapporttabel zijn geladen, worden weergegeven.

Voor PayPal-uitbetalingsrapporten is het verwachte resultaat een vertraging van 24 tot 48 uur vanwege de afhankelijkheid van het tijdpad voor het publiceren van gegevens van PayPal.
