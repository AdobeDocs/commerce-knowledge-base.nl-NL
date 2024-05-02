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

Geplande updates voor een opslaginhoudselement (pagina, product, blok, enz.) niet direct na de begintijd van de update worden weergegeven in de winkel. Dit gebeurt wanneer updates gepland zijn gebruikend [Inhoud stapelen](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) functionaliteit.

## Oorzaak

Vanwege de functie voor zacht leegmaken van Fastly (standaard ingeschakeld) ontvangt de Adobe Commerce-winkel nog steeds de oude (standaard) cacheinhoud wanneer deze wordt verzonden **de eerste** verzoek om het bijgewerkte element snel te verzenden. U hebt snel een tweede aanvraag nodig om de sitegegevens opnieuw te genereren.

Dientengevolge, kan de Fastly schaal inhoud tot het tweede verzoek voor de bijgewerkte inhoud dienen.

**Caching verwacht:** Nadat we een update voor een inhoudselement hebben gepland met behulp van Inhoud opslaan, verzendt Adobe Commerce een verzoek om de cache zo snel mogelijk bij te werken. Hiermee maakt u snel de inhoud van de vorige cache ongeldig (zonder de inhoud te verwijderen) en wordt de bijgewerkte inhoud weergegeven.

**Werkelijke caching:** Als bij ontvangst met Snelheid nog steeds de schaalinhoud wordt gebruikt **de eerste** aanvraag voor de bijgewerkte inhoud, wordt opnieuw gegenereerde, correcte inhoud alleen verzonden na ontvangst **de tweede** verzoek. Dit gedrag is geïmplementeerd om de serverlading te verminderen door de cache alleen te vernieuwen in gebieden met bewezen verkeer, zonder de cache voor de gehele website opnieuw te genereren. Hiermee werkt u de cache geleidelijk bij en bespaart u de toepassingsbronnen.

## Oplossing

Als het serveren van verouderde inhoud zelfs voor het eerste verzoek onacceptabel is, kunt u Zachte zuivering uitschakelen en CMS-pagina leegmaken inschakelen:

1. Meld u als beheerder aan bij uw lokale Commerce-beheerder.
1. Ga naar **Winkels** > **Configuratie** > **Geavanceerd** > **Systeem** > **Volledige paginacache**.
1. Uitbreiden **Snelle configuratie** vervolgens uitvouwen **Geavanceerd**.
1. Set **Zacht leegmaken gebruiken** tot *Nee*.
1. Set **CMS-pagina wissen** tot *Ja*.
1. Klikken **Config opslaan** boven aan de pagina.


![purge_options.png](assets/purge_options.png)

## Gerelateerde documentatie

* [Opties voor leegmaken configureren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in de Commerce on Cloud Infrastructure Guide.
* [Inhoud stapelen](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) in de documentatie bij Inhoud en Ontwerp.
* [Stale inhoud bedienen](https://docs.fastly.com/guides/performance-tuning/serving-stale-content) in Fastly documentatie.
