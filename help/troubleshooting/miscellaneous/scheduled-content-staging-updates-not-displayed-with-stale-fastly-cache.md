---
title: Geplande updates voor het bijhouden van inhoud worden niet weergegeven met een verouderde snelcache
description: Dit artikel bevat een oplossing voor het probleem wanneer in Adobe Commerce-winkels geen geplande updates worden weergegeven bij het gebruik van Inhoud stapelen en Snel. Dit probleem wordt veroorzaakt door de standaardinstelling Snelzacht leegmaken. Deze functie vermindert de belasting van toepassingsbronnen en genereert alleen een nieuwe cache bij een tweede aanvraag. Als u wilt oplossen, kunt u CMS-pagina leegmaken via Commerce Admin inschakelen om altijd opnieuw inhoud te genereren en opnieuw inhoud te leveren.
exl-id: becbffaa-b6dd-4e9b-894e-17901c40223a
feature: CMS, Cache, Page Content, Staging
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# Geplande updates voor het bijhouden van inhoud worden niet weergegeven met een verouderde snelcache

Dit artikel bevat een oplossing voor het probleem wanneer in Adobe Commerce-winkels geen geplande updates worden weergegeven bij het gebruik van Inhoud stapelen en Snel. Dit probleem wordt veroorzaakt door de standaardinstelling Snelzacht leegmaken. Deze functie vermindert de belasting van toepassingsbronnen en genereert alleen een nieuwe cache bij een tweede aanvraag. Als u wilt oplossen, kunt u CMS-pagina leegmaken via Commerce Admin inschakelen om altijd opnieuw inhoud te genereren en opnieuw inhoud te leveren.

## Probleem

Geplande updates voor een opslaginhoudselement (pagina, product, blok, enz.) niet direct na de begintijd van de update worden weergegeven in de winkel. Dit gebeurt wanneer de updates gebruikend de [ Inhoud het Opvoeren ](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) functionaliteit zijn gepland.

## Oorzaak

Wegens de Zachte functionaliteit van de Woorden van de Fastly (die door gebrek wordt toegelaten), ontvangt de opslag van Adobe Commerce nog de oude (oude) caching inhoud wanneer het verzenden van **het eerste** verzoek om de bijgewerkte activa aan Vast. U hebt snel een tweede aanvraag nodig om de sitegegevens opnieuw te genereren.

Dientengevolge, kan de Fastly schaal inhoud tot het tweede verzoek voor de bijgewerkte inhoud dienen.

**Verwachte caching:** Nadat wij een update voor een inhoudsactiva gebruikend Inhoud het Staging plannen, verzendt Adobe Commerce een verzoek om het geheime voorgeheugen aan Vast bij te werken. Hiermee maakt u snel de inhoud van de vorige cache ongeldig (zonder de inhoud te verwijderen) en wordt de bijgewerkte inhoud weergegeven.

**Actual caching:** als de fasly nog de schaalinhoud wanneer het ontvangen van **het eerste** verzoek voor de bijgewerkte inhoud dient, zal het slechts geregenereerde, correcte inhoud verzenden slechts na het ontvangen van **het tweede** verzoek. Dit gedrag is geïmplementeerd om de serverlading te verminderen door de cache alleen te vernieuwen in gebieden met bewezen verkeer, zonder de cache voor de gehele website opnieuw te genereren. Hiermee werkt u de cache geleidelijk bij en bespaart u de toepassingsbronnen.

## Oplossing

Als het serveren van verouderde inhoud zelfs voor het eerste verzoek onacceptabel is, kunt u Zachte zuivering uitschakelen en CMS-pagina leegmaken inschakelen:

1. Meld u als beheerder aan bij uw lokale Commerce-beheerder.
1. Ga naar **Opslag** > **Configuratie** > **Geavanceerd** > **Systeem** > **Volledige het Geheime voorgeheugen van de Pagina**.
1. Vouw **Snelle Configuratie** uit, dan breid **Geavanceerd** uit.
1. Plaats **Zachte Woorden van het Gebruik** aan *Nr*.
1. Plaats **zuiveren CMS pagina** aan *ja*.
1. Klik **sparen Config** bij de bovenkant van de pagina.


![ purge_options.png ](assets/purge_options.png)

## Gerelateerde documentatie

* [ vormt zuiveringsopties ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in Commerce op de Gids van de Infrastructuur van de Wolk.
* [ Inhoud het Opvoeren ](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) in de documentatie van de Inhoud en van het Ontwerp.
* [ het dienen van waliteit inhoud ](https://docs.fastly.com/guides/performance-tuning/serving-stale-content) in Snelle documentatie.
