---
title: Blockers die op Adobe Commerce starten op cloudinfrastructuur
description: Dit artikel biedt een oplossing voor blokkers die op Adobe Commerce kunnen starten op cloudinfrastructuur, zoals problemen met betrekking tot Fastly config, SSL-certificaten, 301 omleidingen en statische prestaties van middelen.
exl-id: 3b2c331f-5d90-4051-ada1-4934538fce79
feature: Cache, Cloud, Marketing Tools, Observability, Paas
role: Developer
source-git-commit: 878abfdc4353122d808929f4834930a16b953e24
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---

# Blockers die op Adobe Commerce starten op cloudinfrastructuur

Dit artikel biedt een oplossing voor blokkers die op Adobe Commerce kunnen starten op cloudinfrastructuur, zoals problemen met betrekking tot Fastly config, SSL-certificaten, 301 omleidingen en statische prestaties van middelen.

## &#x200B;1. Snelle configuratie

[&#x200B; Fastly &#x200B;](https://www.fastly.com/) is een op varens-Gebaseerd Netwerk van de Levering van de Inhoud (CDN) voor het dienen van statische activa. Adobe Commerce is vereist voor cloudinfrastructuur in productieomgevingen. Het is daarom belangrijk om snel te configureren en uw website (UAT) te testen met de snelst ingeschakelde en geconfigureerde omgeving, zowel in Staging- als in Production-omgevingen.

>[!WARNING]
>
>Als FPC (Full Page Cache) is ingeschakeld, werkt de website anders. Zorg ervoor dat u de toepassing test voordat u live gaat.

Het proces van Fastly configuratie wordt gedocumenteerd in detail in het [&#x200B; Snelle onderwerp van de Opstelling &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=nl-NL) in onze gebruikersgids. Hieronder staan de belangrijke stappen.

### 1 bis. Controleer of u de meest recente versie van de module Snelheid hebt geïnstalleerd

Zorg ervoor dat de meest recente versie van de module Snelheid is geïnstalleerd voor de nieuwste functies en verbeteringen. Om te controleren als u de recentste versie van Fastly hebt, herzie [&#x200B; Verbetering de Fastly module &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=nl-NL#upgrade-the-fastly-module) in onze gebruikersgids. Voor meer details, herzie [&#x200B; Opstelling Fastly &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=nl-NL) in onze gebruikersgids.

### 1 ter. Snel inschakelen en configureren met Commerce Admin

Voor meer details, revisie [&#x200B; krijgt uw Fastly geloofsbrieven &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=nl-NL#get-fastly-credentials) in onze gebruikersgids.

### 1 quater. VCL-fragmenten snel uploaden

Voor meer details, zie [&#x200B; VCL aan Fastly &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=nl-NL) in onze gebruikersgids uploaden.

U kunt ook [&#x200B; tot stand brengen en eigen fragmenten van douaneVCL toevoegen &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html?lang=nl-NL).

### 1 quinquies. DNS snel configureren


Verwijs naar dit artikel voor gedetailleerde stappen: [&#x200B; Opstelling Fastly &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=nl-NL#update-dns-configuration-with-development-settings) in onze gebruikersgids.

## &#x200B;2. Geldig SSL-certificaat (TLS)

Probleem: zonder een geldig en werkend SSL-certificaat kunt u geen externe betalingsmethoden testen op de pagina Uitchecken - op de testomgeving.

Aanbeveling **:** vraag uw gedeelde SSL-certificaat om opmaaknamen of Live domeinnamen.


## &#x200B;3. 301 omleidingen configureren en testen

Probleem: 301 omleidingen worden niet opgegeven of zijn slecht geconfigureerd, waardoor je winkel in SEO-classificaties en zoeklijsten valt.

Aanbeveling **:** configureer en test omleidingen zorgvuldig 301.

Als u van een oude website naar een nieuwe migreert, leiden de 301 omleidingen uw klanten van de eerder geïndexeerde oude pagina&#39;s aan de juiste pagina&#39;s op uw nieuwe opslag, als dit:

http://www.mywebsite.com/old-category-page.html **>** http://www.mywebsite.com/new-seo-friendly-category-page.html

**Verwante artikelen:**

* [&#x200B; richt zich door routes.yaml &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/routes/redirects.html?lang=nl-NL) in onze gebruikersgids opnieuw.
* [&#x200B; richt zich door de Console van de Wolk &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=nl-NL) in onze gebruikersgids opnieuw.
* [&#x200B; URL herschrijft &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite.html?lang=nl-NL) in onze gebruikersgids.

## &#x200B;4. Prestaties van activa

Probleem: statische middelen worden langzaam aangeboden, zodat uw site slecht presteert (lange laadtijd, multimedia-inhoud niet weergegeven, enzovoort). Statische elementen van uw website zijn CSS-bronnen, afbeeldingen, video&#39;s, bijgevoegde documenten en nog veel meer. De manier waarop ze zijn georganiseerd en geserveerd, is een belangrijke factor voor de prestaties van uw site.

Aanbeveling: Om mogelijke oorzaken van slechte prestaties te identificeren denk na gebruikend [&#x200B; Toolkit van de Prestaties van Adobe Commerce &#x200B;](https://github.com/magento/magento2/tree/2.3/setup/performance-toolkit) voor prestaties het testen. U zou deze derdehulpmiddelen ook kunnen overwegen:

* [&#x200B; Siege &#x200B;](https://www.joedog.org/siege-home): lading-test en benchmarking van HTTP nut; steunt basisauthentificatie, koekjes, HTTP, HTTPS en de protocollen van FTP.
* [&#x200B; Jmeter &#x200B;](https://jmeter.apache.org/): Een reputatie lading-test en prestaties die hulpmiddel meten. Helpt de prestaties te meten voor verrijkt verkeer, bijvoorbeeld voor flitsverkoop.
* [&#x200B; New Relic &#x200B;](https://support.newrelic.com/): van processen en gebieden van de plaats die langzame prestaties met bijgehouden tijd veroorzaken die per actie wordt doorgebracht, zoals het overbrengen van gegevens, vragen, Redis, enz.
* [&#x200B; WebPageTest &#x200B;](https://www.webpagetest.org/) (vrij) en [&#x200B; (betaald) VK &#x200B;](https://www.pingdom.com/): De analyse in real time van uw plaatspagina&#39;s laadt tijd met verschillende oorsprongsplaatsen.

U kunt [&#x200B; minificatie &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=nl-NL) voor CSS, JavaScript, en HTML ook overwegen.

**Verwante artikelen:**

* [&#x200B; plaatsing van de Test &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie.
