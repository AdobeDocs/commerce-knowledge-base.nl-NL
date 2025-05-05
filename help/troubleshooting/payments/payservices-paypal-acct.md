---
title: PayPal-sandboxaccount niet geverifieerd
description: In dit artikel wordt uitgelegd waarom uw Paypal-sandboxaccount voor Betalingsservices niet is geverifieerd, zodat u de sandbox niet kunt invullen.
exl-id: 05ce130d-6dfe-4834-bdfc-837902100118
feature: Customer Service, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# PayPal-sandboxaccount niet geverifieerd

In dit artikel wordt uitgelegd waarom uw Paypal-sandboxaccount voor Betalingsservices niet is geverifieerd, zodat u de sandbox niet kunt invullen.

## Betrokken producten en versies

* [ de Diensten van de Betaling ](https://marketplace.magento.com/magento-payment-services.html) is nu compatibel met versies 2.4.0 van Adobe Commerce aan 2.4.4.

## Probleem

Onze [ aan boord gaan documentatie ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html?lang=nl-NL) draagt u op om omhoog voor een rekening te ondertekenen PayPal, login de rekening van de Ontwikkelaars van PayPal, en dan een zandbakrekening tot stand te brengen. Als u in het pop-upvenster met PayPal-toegang hebt opgegeven dat u een nieuw account wilt maken tijdens het instappen, kan PayPal uw sandboxaccount niet verifiëren en kunt u de instapprocedure niet voltooien.

<u> Stappen om </u> te reproduceren:

1. U [ installeert de Diensten van de Betaling ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=nl-NL) en [ vormt uw Diensten van Commerce ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html?lang=nl-NL#configure-commerce-services).
1. U navigeert aan **de Diensten van de Betaling** in Admin en [ begin zandbak op het instappen ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html?lang=nl-NL).
1. In PayPal op instapup die verschijnt, creeert u een nieuwe Bedrijfs rekening (in plaats van [ het programma openen met een eerder-gecreeerde Paypal- zandbakrekening ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html?lang=nl-NL#test-in-sandbox-environment) tijdens het instappen.
1. Je hebt PayPal op instapniveau voltooid.
1. In de Admin wordt gemeld dat uw sandboxbetalingen in behandeling zijn en dat u uw e-mailadres met PayPal moet bevestigen om de inboarding te voltooien.

   Je hebt geen bevestigingsbericht ontvangen omdat PayPal je e-mailadres niet kan verifiëren.

## Oorzaak

PayPal kan uw sandboxaccount niet verifiëren en u kunt de sandboxcontrole niet voltooien (wat betekent dat u geen betalingen kunt accepteren of de sandboxmodus kunt testen) als u uw sandboxaccount maakt vóór uw Paypal-account.

## Oplossing

1. Gebruikend een zandbakrekening die in het [ wordt gecreeerd PayPal Developer ](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account) Portaal.
1. Klik [ teruggestelde zandbak ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html?lang=nl-NL#test-in-sandbox-environment) en nieuw begin uw zandbak op het instappen.
1. [ de Steun van het Contact ](mailto:payment-services-support@adobe.com) als u niet uw rekeningskwesties kunt verlichten zodat u onboarding kunt hervatten en betalingen goedkeuren.
