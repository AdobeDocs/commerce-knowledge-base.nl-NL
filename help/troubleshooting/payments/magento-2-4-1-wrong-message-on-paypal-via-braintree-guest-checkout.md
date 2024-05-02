---
title: 'Adobe Commerce 2.4.1: onjuist bericht over uitchecken via PayPal-Braintree voor gasten'
description: In dit artikel wordt een bekende Adobe Commerce 2.4.1-kwestie beschreven. Als uitchecken door gasten is uitgeschakeld, krijgt een gastklant die via Braintree een bestelling probeert te plaatsen met PayPal een niet-informatief foutbericht.
exl-id: 758f5c57-997e-4aca-b299-9934c94fa121
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
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

<u>Vereisten</u>:

1. In de Commerce Admin, onder **Winkels** > **Configuratie** > **Verkoop** > **Afhandeling**, set **Uitchecken door gasten toestaan** = *Nee*.
1. PayPal inschakelen via Braintree zoals beschreven in het dialoogvenster [Braintree](https://docs.magento.com/user-guide/payment/braintree.html?) in onze gebruikershandleiding.

<u>Stappen om te reproduceren</u>:

1. Voeg product toe aan winkelwagentje als gast.
1. Selecteren **Minikaart** en klik op **Betalen met PayPal**.
1. Voltooi de PayPal-afhandeling en start vervolgens op de pagina Order Review.
1. Selecteren **Verzendmethode**.
1. Klikken **Opdracht plaatsen**.

<u>Verwachte resultaten</u>:

Wanneer een klant op de PayPal-knop op de pagina Miniwinkelwagentje of Winkelwagentje klikt, moet het volgende bericht aan de klant worden getoond:

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

Als u Direct PayPal inschakelt zonder Braintree te gebruiken, gedraagt dit scenario zich anders. Het staat de gastgebruiker niet toe om met het betalingsproces verder te gaan. Het volgende bericht wordt weergegeven wanneer de gastgebruiker op de PayPal-knop in de Mini-cart klikt:

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

<u>Werkelijke resultaten</u>:

De klant wordt omgeleid naar de pagina Winkelwagentje en het volgende bericht wordt weergegeven:

<pre><code class="language-bash">The customer email is missing. Enter and try again.</code></pre>

## Workaround

De oplossing voor deze kwestie is dat de klant zich bij een opslag kan aanmelden (de geregistreerde gebruikers gebruiken geen gastcontrole.) waarbij uitchecken door gasten is uitgeschakeld. Dit probleem is opgelost in Adobe Commerce versie 2.4.2.

## Gerelateerde lezing

* [Beste praktijken voor het aantal producten in karretjes in Adobe Commerce](https://support.magento.com/hc/en-us/articles/360048550332) in onze kennisbasis voor ondersteuning.
* [Zelfstudie voor het verwerken van bestellingen: stap 1. Items aan het winkelwagentje toevoegen](https://devdocs.magento.com/guides/v2.4/rest/tutorials/orders/order-add-items.html) in onze documentatie voor ontwikkelaars
* [GraphQL-zelfstudie over uitchecken: stap 1. Producten aan de winkelwagentje toevoegen](https://devdocs.magento.com/guides/v2.4/graphql/tutorials/checkout/checkout-add-product-to-cart.html) in onze documentatie voor ontwikkelaars
