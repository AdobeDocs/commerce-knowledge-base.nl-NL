---
title: robots.txt geeft 404 fouten in Adobe Commerce op cloudinfrastructuur
description: Dit artikel biedt een oplossing voor het probleem wanneer in het bestand 'robots.txt' een fout van 404 wordt gegenereerd in Adobe Commerce op cloudinfrastructuur.
exl-id: 6f0b9f47-1901-4c43-88d8-fd992015d70f
feature: Cloud, Marketing Tools, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# robots.txt geeft 404 fouten in Adobe Commerce op cloudinfrastructuur

Dit artikel bevat een oplossing voor het `robots.txt` Er treedt een fout van 404 op in Adobe Commerce op de cloudinfrastructuur.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur (alle versies)

## Probleem

De `robots.txt` werkt niet en genereert een Nginx-uitzondering. De `robots.txt` bestand wordt dynamisch &quot;ter plekke&quot; gegenereerd. De `robots.txt` bestand is niet toegankelijk voor de `/robots.txt` URL omdat Nginx een herschrijfregel heeft die alle regels forceert omleiden `/robots.txt` verzoeken aan de `/media/robots.txt` niet bestaat.

## Oorzaak

Dit gebeurt typisch wanneer Nginx niet behoorlijk wordt gevormd.

## Oplossing

De oplossing is om de regel van Nginx onbruikbaar te maken die opnieuw richt `/robots.txt` verzoeken aan de `/media/robots.txt` bestand. De handelaren met toegelaten zelfbediening kunnen het op hun eigen doen, en de handelaren zonder zelf-dienst toegelaten behoefte om een steunkaartje tot stand te brengen.

Als de zelfbediening niet is ingeschakeld (of niet zeker of deze is ingeschakeld), [een Magento-ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) verzoek om verwijdering van de Nginx-omleidingsregel uit `/robots.txt` verzoeken om `/media/robots.txt`.

Als u de zelfbediening hebt toegelaten, gelieve ECE-Hulpmiddelen aan minstens 2002.0.12 te bevorderen en de Nginx te verwijderen omleidingsregel in uw `.magento.app.yaml` bestand. U kunt verwijzen naar [Robots voor site-toewijzing en zoekprogramma&#39;s toevoegen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap.html) in onze ontwikkelaarsdocumentatie voor meer informatie.

## Verwante lezing

* [Hoe te om kwaadwillig verkeer voor Magento Commerce Cloud op Fastly te blokkeren](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) in onze kennisbasis voor ondersteuning.
* [Robots voor site-toewijzing en zoekprogramma&#39;s toevoegen](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) in onze ontwikkelaarsdocumentatie.
* [Zoekmachinekrobots](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots) in onze gebruikershandleiding.
