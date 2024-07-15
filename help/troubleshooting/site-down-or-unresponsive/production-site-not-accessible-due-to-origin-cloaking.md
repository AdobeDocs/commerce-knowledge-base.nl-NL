---
title: Site is niet toegankelijk vanwege camouflage van oorsprong
description: Dit artikel biedt een oplossing voor het geval dat uw Adobe Commerce op de opslaglocatie van de cloudinfrastructuur of productiesite en/of Admin niet toegankelijk is.
exl-id: 4412d744-3066-4f78-bc45-8149614ce455
feature: Products
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# Site is niet toegankelijk vanwege camouflage van oorsprong

Dit artikel biedt een oplossing voor het geval dat uw Adobe Commerce op de opslaglocatie van de cloudinfrastructuur of productiesite en/of Admin niet toegankelijk is.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur 2.3.x, 2.4.x

## Probleem

https: &#x200B;//mydomain.com.c.&lt;projectid>.magento.cloud/ is niet meer toegankelijk.

<u> Stappen om te reproduceren:</u>

1. Meld u aan bij uw project.
1. Klik **Project van de Toegang** voor een lijst van URLs en SSH.

<u> Ware resultaten:</u>

Pagina kan niet worden geladen met de volgende fout:

*NET::ERR\_CERT\_INVALID* *waakzaam TLS, slecht certificaat (554):*

<u> Verwachte resultaten:</u>

Pagina is geladen.

## Oorzaak

De functie Oorsprong camoufleren is ingeschakeld, zodat de oorsprong niet langer rechtstreeks toegankelijk is.

Oorspronkelijke camouflage is een beveiligingsfunctie waarmee Adobe Commerce elk niet-snel verkeer naar de cloudinfrastructuur (herkomst) kan blokkeren om DDoS-aanvallen te voorkomen.

## Oplossing

* Schakel over naar https://mydomain.com/ als uw cloudsite actief is.
* Als u een actieve plaats (niet wolk) hebt, gebruikend het https://mydomain.com/ domein, opstelling een subdomein `mcprod.mydomain.com` en werk uw **Basis URL** aan *https://mcprod.mydomain.com* in plaats daarvan bij, dan [ richt DNS aan Fastly ](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#update-dns-configuration-with-development-settings).

## Gerelateerde lezing

[ Snelle oorsprong het camoufleren FAQ ](/help/faq/general/fastly-origin-cloaking-enablement-faq.md) in onze basis van steunkennis.
