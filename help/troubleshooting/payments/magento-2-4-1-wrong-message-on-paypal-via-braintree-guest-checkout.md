---
title: 'Adobe Commerce 2.4.1: onjuist bericht over uitchecken via PayPal-Braintree voor gasten'
description: In dit artikel wordt een bekende Adobe Commerce 2.4.1-kwestie beschreven. Als uitchecken door gasten is uitgeschakeld, krijgt een gastklant die via Braintree een bestelling probeert te plaatsen met PayPal een niet-informatief foutbericht.
exl-id: 758f5c57-997e-4aca-b299-9934c94fa121
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Adobe Commerce 2.4.1: onjuist bericht over uitchecken via PayPal-Braintree voor gasten

In dit artikel wordt een bekende Adobe Commerce 2.4.1-kwestie beschreven. Als uitchecken door gasten is uitgeschakeld, krijgt een gastklant die via Braintree een bestelling probeert te plaatsen met PayPal een niet-informatief foutbericht.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.0, 2.4.1
* Adobe Commerce on cloud Infrastructure 2.4.0, 2.4.1

## Probleem

Er wordt een niet-specifieke fout weergegeven wanneer uitchecken door gasten vanaf de achterkant is uitgeschakeld en de betalingsoptie PayPal via Braintree is geselecteerd in de miniwinkelwagentje of winkelwagentje.

<u> Eerste vereisten </u>:

1. In Commerce Admin, onder **Slaat** > **Configuratie** > **Verkoop** > **Controle**, plaats **Gast Afhandeling** = *Nr* toestaan.
1. Laat PayPal door Braintree toe zoals die in de [ Braintree ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/payments/braintree?) in onze gebruikersgids wordt beschreven.

<u> Stappen om </u> te reproduceren:

1. Voeg product toe aan winkelwagentje als gast.
1. Selecteer **mini-kar** en klik **Betalen met PayPal**.
1. Voltooi de PayPal-afhandeling en start vervolgens op de pagina Order Review.
1. Selecteer **Verzendmethode**.
1. Klik **de Orde van de Plaats**.

<u> Verwachte resultaten </u>:

Wanneer een klant op de PayPal-knop op de pagina Miniwinkelwagentje of Winkelwagentje klikt, moet het volgende bericht aan de klant worden getoond:

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

Als u Direct PayPal inschakelt zonder Braintree te gebruiken, gedraagt dit scenario zich anders. Het staat de gastgebruiker niet toe om met het betalingsproces verder te gaan. Het volgende bericht wordt weergegeven wanneer de gastgebruiker op de PayPal-knop in de Mini-cart klikt:

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

<u> Ware resultaten </u>:

De klant wordt omgeleid naar de pagina Winkelwagentje en het volgende bericht wordt weergegeven:

<pre><code class="language-bash">The customer email is missing. Enter and try again.</code></pre>

## Workaround

De oplossing voor deze kwestie is dat de klant zich bij een opslag kan aanmelden (de geregistreerde gebruikers gebruiken geen uitchecksysteem voor gasten.) waar de gastcontrole wordt onbruikbaar gemaakt. Dit probleem is opgelost in Adobe Commerce versie 2.4.2.

## Gerelateerde lezing

* [ Beste praktijken voor aantal producten in kar in Adobe Commerce ](https://support.magento.com/hc/en-us/articles/360048550332) in onze basis van steunkennis.
* [ de verwerkingsleerprogramma van de Orde: Stap 1. Voeg punten aan de kar ](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/order-add-items/) in onze ontwikkelaarsdocumentatie toe
* [ GraphQL checkout leerprogramma: Stap 1. Voeg producten aan de kar ](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/checkout-add-product-to-cart.html) in onze ontwikkelaarsdocumentatie toe
