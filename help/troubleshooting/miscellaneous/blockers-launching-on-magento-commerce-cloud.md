---
title: Blockers die op Adobe Commerce starten op cloudinfrastructuur
description: Dit artikel biedt een oplossing voor blokkers die op Adobe Commerce kunnen starten op cloudinfrastructuur, zoals problemen met betrekking tot Fastly config, SSL-certificaten, 301 omleidingen en statische prestaties van middelen.
exl-id: 3b2c331f-5d90-4051-ada1-4934538fce79
feature: Cache, Cloud, Marketing Tools, Observability, Paas
role: Developer
source-git-commit: 3dd44b72bc9f02fe808b70355c4331fc28aa3606
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 0%

---

# Blockers die op Adobe Commerce starten op cloudinfrastructuur

Dit artikel biedt een oplossing voor blokkers die op Adobe Commerce kunnen starten op cloudinfrastructuur, zoals problemen met betrekking tot Fastly config, SSL-certificaten, 301 omleidingen en statische prestaties van middelen.

## 1. Snelle configuratie

[ Fastly ](https://www.fastly.com/) is een op varens-Gebaseerd Netwerk van de Levering van de Inhoud (CDN) voor het dienen van statische activa. Adobe Commerce is vereist voor cloudinfrastructuur in productieomgevingen. Het is daarom belangrijk om snel te configureren en uw website (UAT) te testen met de snelst ingeschakelde en geconfigureerde omgeving, zowel in Staging- als in Production-omgevingen.

>[!WARNING]
>
>Als FPC (Full Page Cache) is ingeschakeld, werkt de website anders. Zorg ervoor dat u de toepassing test voordat u live gaat.

Het proces van Fastly configuratie wordt gedocumenteerd in detail in het [ Snelle onderwerp van de Opstelling ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in onze gebruikersgids. Hieronder staan de belangrijke stappen.

### 1 bis. Controleer of u de meest recente versie van de module Snelheid hebt geïnstalleerd

Zorg ervoor dat de meest recente versie van de module Snelheid is geïnstalleerd voor de nieuwste functies en verbeteringen. Om te controleren als u de recentste versie van Fastly hebt, herzie [ Verbetering de Fastly module ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upgrade-the-fastly-module) in onze gebruikersgids. Voor meer details, herzie [ Opstelling Fastly ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in onze gebruikersgids.

### 1 ter. Snel inschakelen en configureren met Commerce Admin

Voor meer details, revisie [ krijgt uw Fastly geloofsbrieven ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials) in onze gebruikersgids.

### 1 quater. VCL-fragmenten snel uploaden

Voor meer details, zie [ VCL aan Fastly ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in onze gebruikersgids uploaden.

U kunt ook [ tot stand brengen en eigen fragmenten van douaneVCL toevoegen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html).

### 1 quinquies. DNS snel configureren


Verwijs naar dit artikel voor gedetailleerde stappen: [ Opstelling Fastly ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings) in onze gebruikersgids.

### Verwante Fastartikelen in onze basis van supportkennis

* [Snel in cache plaatsen werkt niet op Cloud](/help/troubleshooting/miscellaneous/fastly-caching-is-not-working-on-magento-cloud.md)
* [Fout bij snel leegmaken van cache op Cloud (de aanvraag voor leegmaken is niet verwerkt)](/help/troubleshooting/miscellaneous/error-purging-fastly-cache-on-cloud-the-purge-request-was-not-processed-successfully.md)

## 2. Geldig SSL-certificaat (TLS)

Probleem: zonder een geldig en werkend SSL-certificaat kunt u geen externe betalingsmethoden testen op de pagina Uitchecken - op de testomgeving.

Aanbeveling **:** vraag uw gedeelde SSL-certificaat om opmaaknamen of Live domeinnamen.

Lees over SSL certificaten in dit [ Snelle FAQ ](/help/announcements/adobe-commerce-announcements/magento-ssl-tls-certificate-requirements-and-clean-up.md) artikel van FAQ in onze basis van de steunkennis.

## 3. 301 omleidingen configureren en testen

Probleem: 301 omleidingen worden niet opgegeven of zijn slecht geconfigureerd, waardoor je winkel in SEO-classificaties en zoeklijsten valt.

Aanbeveling **:** configureer en test omleidingen zorgvuldig 301.

Als u van een oude website naar een nieuwe migreert, leiden de 301 omleidingen uw klanten van de eerder geïndexeerde oude pagina&#39;s aan de juiste pagina&#39;s op uw nieuwe opslag, als dit:

http://www.mywebsite.com/old-category-page.html **>** http://www.mywebsite.com/new-seo-friendly-category-page.html

**Verwante artikelen:**

* [ richt zich door routes.yaml ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/routes/redirects.html) in onze gebruikersgids opnieuw.
* [ richt zich door de Console van de Wolk ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) in onze gebruikersgids opnieuw.
* [ URL herschrijft ](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite.html) in onze gebruikersgids.

## 4. Prestaties van activa

Probleem: statische middelen worden langzaam aangeboden, zodat uw site slecht presteert (lange laadtijd, multimedia-inhoud niet weergegeven, enzovoort). Statische elementen van uw website zijn CSS-bronnen, afbeeldingen, video&#39;s, bijgevoegde documenten en nog veel meer. De manier waarop ze zijn georganiseerd en geserveerd, is een belangrijke factor voor de prestaties van uw site.

Aanbeveling: Om mogelijke oorzaken van slechte prestaties te identificeren denk na gebruikend [ Toolkit van de Prestaties van Adobe Commerce ](https://github.com/magento/magento2/tree/2.3/setup/performance-toolkit) voor prestaties het testen. U zou deze derdehulpmiddelen ook kunnen overwegen:

* [ Siege ](https://www.joedog.org/siege-home/): lading-test en benchmarking van HTTP nut; steunt basisauthentificatie, koekjes, HTTP, HTTPS en de protocollen van FTP.
* [ Jmeter ](https://jmeter.apache.org/): Een reputatie lading-test en prestaties die hulpmiddel meten. Helpt de prestaties te meten voor verrijkt verkeer, bijvoorbeeld voor flitsverkoop.
* [ New Relic ](https://support.newrelic.com/): van processen en gebieden van de plaats die langzame prestaties met bijgehouden tijd veroorzaken die per actie wordt doorgebracht, zoals het overbrengen van gegevens, vragen, Redis, enz.
* [ WebPageTest ](https://www.webpagetest.org/) (vrij) en [ (betaald) VK ](https://www.pingdom.com/): De analyse in real time van uw plaatspagina&#39;s laadt tijd met verschillende oorsprongsplaatsen.

U kunt [ minificatie ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) voor CSS, JavaScript, en HTML ook overwegen.

**Verwante artikelen:**

* [ plaatsing van de Test ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production.html) in onze ontwikkelaarsdocumentatie.
