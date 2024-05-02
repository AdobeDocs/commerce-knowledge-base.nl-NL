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

[Snel](https://www.fastly.com/) is een op Varnish-Gebaseerd Netwerk van de Levering van de Inhoud (CDN) voor het dienen van statische activa. Adobe Commerce is vereist voor cloudinfrastructuur in productieomgevingen. Het is daarom belangrijk om snel te configureren en uw website (UAT) te testen met de snelst ingeschakelde en geconfigureerde omgeving, zowel in Staging- als in Production-omgevingen.

>[!WARNING]
>
>Als FPC (Full Page Cache) is ingeschakeld, werkt de website anders. Zorg ervoor dat u de toepassing test voordat u live gaat.

Het proces van Fastly configuratie wordt in detail gedocumenteerd in [Snel instellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in onze gebruikershandleiding. Hieronder staan de belangrijke stappen.

### 1 bis. Controleer of u de meest recente versie van de module Snelheid hebt geïnstalleerd

Zorg ervoor dat de meest recente versie van de module Snelheid is geïnstalleerd voor de nieuwste functies en verbeteringen. Als u wilt controleren of u over de nieuwste versie van Snelheid beschikt, raadpleegt u [De module Snelheid upgraden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upgrade-the-fastly-module) in onze gebruikershandleiding. Voor meer informatie raadpleegt u [Snel instellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in onze gebruikershandleiding.

### 1 ter. Snel inschakelen en configureren met Commerce Admin

Voor meer informatie raadpleegt u [Krijg uw snelle geloofsbrieven](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials) in onze gebruikershandleiding.

### 1 quater. VCL-fragmenten snel uploaden

Zie voor meer informatie [VCL snel uploaden naar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in onze gebruikershandleiding.

U kunt [eigen aangepaste VCL-fragmenten maken en toevoegen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html).

### 1 quinquies. DNS snel configureren


Raadpleeg dit artikel voor gedetailleerde stappen: [Snel instellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings) in onze gebruikershandleiding.

### Verwante Fastartikelen in onze basis van supportkennis

* [Snel in cache plaatsen werkt niet op Cloud](/help/troubleshooting/miscellaneous/fastly-caching-is-not-working-on-magento-cloud.md)
* [Fout bij snel leegmaken van cache op Cloud (de aanvraag voor leegmaken is niet verwerkt)](/help/troubleshooting/miscellaneous/error-purging-fastly-cache-on-cloud-the-purge-request-was-not-processed-successfully.md)

## 2. Geldig SSL-certificaat (TLS)

Probleem: zonder een geldig en werkend SSL-certificaat kunt u geen externe betalingsmethoden testen op de pagina Uitchecken - op de testomgeving.

Aanbeveling **:** Vraag uw gedeelde SSL-certificaat aan voor Staging- of Live-domeinnamen.

Meer informatie over SSL-certificaten vindt u in deze [Snelle veelgestelde vragen](/help/announcements/adobe-commerce-announcements/magento-ssl-tls-certificate-requirements-and-clean-up.md) artikel in onze kennisbasis voor ondersteuning.

## 3. 301 omleidingen configureren en testen

Probleem: 301 omleidingen worden niet opgegeven of zijn slecht geconfigureerd, waardoor je winkel in SEO-classificaties en zoeklijsten valt.

Aanbeveling **:** Configureer en test de 301 omleidingen zorgvuldig.

Als u van een oude website naar een nieuwe migreert, leiden de 301 omleidingen uw klanten van de eerder geïndexeerde oude pagina&#39;s aan de juiste pagina&#39;s op uw nieuwe opslag, als dit:

http://www.mywebsite.com/old-category-page.html **>** http://www.mywebsite.com/new-seo-friendly-category-page.html

**Verwante artikelen:**

* [Omleiding door routes.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/routes/redirects.html) in onze gebruikershandleiding.
* [Omleiden via de Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) in onze gebruikershandleiding.
* [URL herschrijft](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite.html) in onze gebruikershandleiding.

## 4. Prestaties van activa

Probleem: statische middelen worden langzaam aangeboden, zodat uw site slecht presteert (lange laadtijd, multimedia-inhoud niet weergegeven, enzovoort). Statische elementen van uw website zijn CSS-bronnen, afbeeldingen, video&#39;s, bijgevoegde documenten en nog veel meer. De manier waarop ze zijn georganiseerd en geserveerd, is een belangrijke factor voor de prestaties van uw site.

Aanbeveling: om mogelijke oorzaken van slechte prestaties te identificeren, kunt u overwegen [Adobe Commerce Performance Toolkit](https://github.com/magento/magento2/tree/2.3/setup/performance-toolkit) voor prestatietests. U zou deze derdehulpmiddelen ook kunnen overwegen:

* [Siege](https://www.joedog.org/siege-home/): Hulpprogramma voor het testen en benchmarken van HTTP-taken; ondersteunt basisverificatie, cookies, HTTP-, HTTPS- en FTP-protocollen.
* [Jmeter](https://jmeter.apache.org/): Een betrouwbare tool voor het meten van de belasting en prestaties. Helpt de prestaties te meten voor verrijkt verkeer, bijvoorbeeld voor flitsverkoop.
* [New Relic](https://support.newrelic.com/): Hiermee zoekt u processen en gebieden van de site die leiden tot trage prestaties met bijgehouden tijd per actie, zoals het verzenden van gegevens, query&#39;s, Redis, enzovoort.
* [WebPageTest](https://www.webpagetest.org/) (gratis) en [VK](https://www.pingdom.com/) (betaald): Real-time analyse van uw sitepagina&#39;s laadt tijd met verschillende oorspronkelijke locaties.

U kunt ook [miniatuur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) voor CSS, JavaScript en HTML.

**Verwante artikelen:**

* [Implementatie testen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production.html) in onze ontwikkelaarsdocumentatie.
