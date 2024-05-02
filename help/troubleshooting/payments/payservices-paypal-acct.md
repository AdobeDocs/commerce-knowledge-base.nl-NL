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

* [Betalingsdiensten](https://marketplace.magento.com/magento-payment-services.html) is nu compatibel met Adobe Commerce-versies 2.4.0 tot en met 2.4.4.

## Probleem

Ons [documentatie over instapkaarten](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html) Hiermee kunt u zich aanmelden voor een PayPal-account, zich aanmelden bij de Paypal Developers-account en vervolgens een sandboxaccount maken. Als u in het pop-upvenster met PayPal-toegang hebt opgegeven dat u een nieuw account wilt maken tijdens het instappen, kan PayPal uw sandboxaccount niet verifiëren en kunt u de instapprocedure niet voltooien.

<u>Stappen om te reproduceren</u>:

1. U [Betalingsservices installeren](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) en [Commerce Services configureren](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-commerce-services).
1. Ga naar **Betalingsdiensten** in de Admin en [start sandbox on boarding](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html).
1. In het pop-upvenster PayPal on boarding maakt u een nieuwe Business-account (in plaats van [aanmelden met een eerder gemaakt PayPal-sandboxaccount](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) tijdens het instappen.
1. Je hebt PayPal op instapniveau voltooid.
1. In de Admin wordt gemeld dat uw sandboxbetalingen in behandeling zijn en dat u uw e-mailadres met PayPal moet bevestigen om de inboarding te voltooien.

   Je hebt geen bevestigingsbericht ontvangen omdat PayPal je e-mailadres niet kan verifiëren.

## Oorzaak

PayPal kan uw sandboxaccount niet verifiëren en u kunt de sandboxcontrole niet voltooien (wat betekent dat u geen betalingen kunt accepteren of de sandboxmodus kunt testen) als u uw sandboxaccount maakt vóór uw Paypal-account.

## Oplossing

1. Een sandboxaccount gebruiken die is gemaakt in het dialoogvenster [PayPal-ontwikkelaar](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account) Portaal.
1. Klikken [sandbox opnieuw instellen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) en start de sandbox opnieuw aan boord.
1. [Contact opnemen met ondersteuning](mailto:payment-services-support@adobe.com) als je je accountproblemen niet kunt verhelpen, zodat je het instappen kunt hervatten en betalingen kunt accepteren.
