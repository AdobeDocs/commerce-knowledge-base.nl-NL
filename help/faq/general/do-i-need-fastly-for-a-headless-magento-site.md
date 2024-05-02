---
title: Heb ik Fastly nodig voor een Adobe Commerce-site zonder Headless?
description: Heb ik Fastly nodig voor een Adobe Commerce-site zonder Headless?
exl-id: d7e07160-6a61-4c03-8f8c-4f879d86ea44
feature: Cache, GraphQL, Compliance
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Heb ik Fastly nodig voor een Adobe Commerce-site zonder Headless?

>[!NOTE]
>
>Alle klanten moeten snel voor hun productie en het opvoeren milieu&#39;s gebruiken. Het is snel een Netwerk van de Levering van de Inhoud (CDN) dat volledige pagina in cache plaatsen, beeldoptimalisering, en de veiligheidsdiensten (DDoS en WAF) als deel van uw Adobe Commerce op de projecten van de wolkeninfrastructuur verleent. Dit zijn de kernonderdelen van de Adobe Commerce-oplossing, die betere prestaties en beveiliging bieden. Deze functies maken deel uit van de PCI-compatibiliteit van de Adobe. U moet deze snelservices instellen voor uw Starter Master-, Staging-, Pro Staging- en Productomgevingen. Als u Adobe Commerce gebruikt voor een headless-implementatie, moet al het API-verkeer van het openbare internet snel worden doorgegeven. We raden u dan ook aan snel GraphQL-reacties in het cachegeheugen op te slaan. Zie [GraphQL Developer Guide > Caching with Fastly](https://devdocs.magento.com/guides/v2.3/graphql/caching.html#caching-with-fastly) in onze ontwikkelaarsdocumentatie.

## **Vraag**

Ik ben bezig met de ontwikkeling van een eindeloze uitvoering van Adobe Commerce. Moet ik nog als dienst CDN voor het snel gebruiken?

## **Antwoord**

Nee, dat doe je niet. In deze situatie kunt u snel overslaan, tenminste in het begin van de ontwikkeling.

De enige situatie u niet kunt willen toelaten is voor een headless plaatsing.
Zie [Cloud voor Adobe Commerce > Fastly](https://devdocs.magento.com/cloud/cdn/cloud-fastly.html) in onze ontwikkelaarsdocumentatie.

Maar hoogstwaarschijnlijk hebt u het SSL-certificaat snel nodig.

Alle Adobe Commerce-klanten met cloudinfrastructuur krijgen van Fastly een gedeeld SSL-certificaat als onderdeel van het abonnement op de cloud. Het toevoegen van een eigen SSL-certificaat aan Fastly is een aparte en goedkoop betaalmiddel. Daarom raden we u ten zeerste aan om Fastly in te schakelen en deze minstens te testen op Staging and Production-omgevingen voordat u live gaat - zelfs voor uw Adobe Commerce-website zonder kop.

## Meer informatie

* [Headless Websites: Wat is de Big Deal met ontkoppelde architectuur?](https://pantheon.io/blog/headless-websites-whats-big-deal-decoupled-architecture) door [Josh Koenig](https://pantheon.io/team/josh-koenig).
* [Snel](https://devdocs.magento.com/cloud/cdn/cloud-fastly.html) in onze ontwikkelaarsdocumentatie.
