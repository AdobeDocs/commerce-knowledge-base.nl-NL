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

Dit artikel bevat een oplossing voor het probleem wanneer in het `robots.txt` -bestand een fout van 404 optreedt in Adobe Commerce op de cloud-infrastructuur.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur (alle versies)

## Probleem

Het bestand `robots.txt` werkt niet en genereert een Nginx-uitzondering. Het `robots.txt` -bestand wordt dynamisch &quot;ter plekke&quot; gegenereerd. Het `robots.txt` -bestand is niet toegankelijk via de `/robots.txt` URL omdat Nginx een herschrijfregel heeft die alle `/robots.txt` -aanvragen forceert omleiden naar het `/media/robots.txt` -bestand dat niet bestaat.

## Oorzaak

Dit gebeurt typisch wanneer Nginx niet behoorlijk wordt gevormd.

## Oplossing

De oplossing is het uitschakelen van de regel Nginx die `/robots.txt` -aanvragen doorstuurt naar het `/media/robots.txt` -bestand. De handelaren met toegelaten zelfbediening kunnen het op hun eigen doen, en de handelaren zonder zelf-dienst toegelaten behoefte om een steunkaartje tot stand te brengen.

Als u niet de toegelaten zelfbediening hebt (of niet zeker als het) toeliet, [ voorlegt een kaartje van de Steun van het Magento ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) verzoekend schrapping van de Nginx omleidingsregel van `/robots.txt` verzoeken aan `/media/robots.txt`.

Als u de zelfbediening hebt ingeschakeld, werkt u ECE-Tools bij naar minimaal 2002.0.12 en verwijdert u de Nginx-omleidingsregel in uw `.magento.app.yaml` -bestand. U kunt naar [ verwijzen voeg plaatstoewijzing en onderzoekmachine robots ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap.html) in onze ontwikkelaarsdocumentatie voor meer informatie toe.

## Verwante lezing

* [ hoe te om kwaadwillig verkeer voor Magento Commerce Cloud op Fastly niveau ](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) in onze steunkennisbasis te blokkeren.
* [ voeg plaatstoewijzing en onderzoekmachine robots ](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) in onze ontwikkelaarsdocumentatie toe.
* [ Robots van de Motor van het Onderzoek ](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots) in onze gebruikersgids.
