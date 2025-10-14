---
title: Klanten worden afgemeld of krijgen inhoud van winkelwagentje kwijt in Adobe Commerce
description: Dit artikel biedt een oplossing en oplossing voor het probleem, waarbij klanten hun product uit het winkelwagentje op de winkel verliezen of afmelden nadat ze van betaling of andere services van derden naar de Adobe Commerce-winkel zijn omgeleid (sessiecookie "raakt verloren").
exl-id: 9175570c-b06c-4a65-b8ca-7a12ff266afb
feature: Orders, Page Content, Shopping Cart, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# Klanten worden afgemeld of krijgen inhoud van winkelwagentje kwijt in Adobe Commerce

Dit artikel biedt een oplossing voor het probleem, waarbij klanten hun product uit het winkelwagentje op de winkel verliezen of afmelden nadat ze van betaling of andere services van derden naar de Adobe Commerce Store zijn omgeleid (sessiecookie &quot;raakt verloren&quot;).

## Betrokken producten en versies

* Adobe Commerce op-gebouw, [&#x200B; alle gesteunde versies &#x200B;](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Adobe Commerce op wolkeninfrastructuur, [&#x200B; alle gesteunde versies &#x200B;](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Probleem

<u> Stappen om te reproduceren:</u>

1. De klant voegt producten toe aan winkelwagentje en gaat verder met het afrekenen.
1. De klant wordt doorgestuurd naar de externe site voor betaling/verzending of andere informatie/service.
1. De klant wordt teruggeleid naar de winkel.

<u> Ware resultaat:</u>

De klant is omgeleid naar het lege winkelwagentje of een lege pagina.

<u> Verwacht resultaat:</u>

De klant is omgeleid naar een pagina voor een geslaagde betaling (of een andere succespagina), zonder dat de gegevens en voortgang van de afhandeling verloren gaan.

## Oorzaak

Het het koekjesattribuut van SameSite wordt geplaatst aan *Lax* of niet gespecificeerd (die als reeks aan *Lax* wordt behandeld). Het hebben van `SameSite` = *Lax* maakt het overbrengen van een koekje naar externe URLs via `POST` verzoeken onbruikbaar.

## Oplossing

Om de kwestie op te lossen, contacteer de derdedienstverlener en verzoek hun ontwikkelaars om hun integratie bij te werken om koekjesparameters te vormen.

## Gerelateerde lezing

[&#x200B; update Chrome SameSite &#x200B;](https://www.chromestatus.com/feature/5088147346030592)
