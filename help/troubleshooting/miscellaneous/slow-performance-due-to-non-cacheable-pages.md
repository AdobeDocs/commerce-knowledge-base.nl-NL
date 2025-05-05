---
title: Trage prestaties door niet-cacheable pagina's
description: Dit artikel biedt oplossingen voor langere laadtijden of uitvallen van de website omdat de volledige paginacache (bijvoorbeeld Snelst) is uitgeschakeld voor elk blok op elke pagina die in de cache moet worden geplaatst.
exl-id: 7401d9bd-710c-4221-9c3d-d78042c1c1ad
feature: Cache, Categories
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# Trage prestaties door niet-cacheable pagina&#39;s

Dit artikel biedt oplossingen voor langere laadtijden of uitvallen van de website omdat de volledige paginacache (bijvoorbeeld Snelst) is uitgeschakeld voor elk blok op elke pagina die in de cache moet worden geplaatst.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur 2.x.x
* Adobe Commerce op locatie 2.x.x

### Probleem

De site heeft te maken met trage prestaties omdat er cacheblokken op pagina&#39;s zijn die in cache moeten kunnen worden opgeslagen, maar die zijn ingesteld op `cacheable="false"` .

### Oorzaak

Er zijn pagina&#39;s die in cache moeten worden geplaatst door Adobe Commerce. Deze pagina&#39;s hebben de grootste doorvoer. Bij elk verzoek van dit type pagina&#39;s in plaats van uit cache, wordt Adobe Commerce langzamer uitgevoerd.

Deze pagina&#39;s zijn:

* Cataloguscategorie (PLP)
* Pagina met productdetails (PDP)
* Statische pagina&#39;s met inhoud (startpagina, contact met ons, enz.)

In cache plaatsen en niet in cache plaatsen zijn termen die worden gebruikt om aan te geven of een pagina al dan niet in cache moet worden geplaatst. Standaard zijn alle pagina&#39;s in cache geplaatst. Als een blok in een lay-out echter als niet-cacheable is aangewezen, is de gehele pagina niet-cacheable.

In de onderstaande schermafbeelding ziet u een blok met de instelling `cacheable="false"` **&#x200B; *** waarmee een oncachebare pagina wordt gemaakt.

![ non_cacheable_kb.png ](assets/non_cacheable_kb.png)

Voorbeelden van pagina&#39;s die niet in cache kunnen worden geplaatst, zijn vergelijkingsproducten, winkelwagentjes en uitcheckpagina&#39;s.

De volgende lijst met pagina&#39;s wordt niet in cache geplaatst (caches voor snellen, blokkeren en lay-out worden vermeden.) Dit komt door de &quot;cacheable&quot;configuratie in lay-out voor.

### Oplossing

Controleer of voor de hierboven opgegeven bestanden de instelling `cacheable="false"` is ingesteld. Als dat het geval is, controleert u of deze instelling nodig is of vereist is.

* Indien nodig, denk na bewegend niet-cacheable blokken aan [ privé inhoudsmechanisme ](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) in plaats daarvan.
* Verwijder indien nodig het kenmerk `cacheable="false"` en verwijder de lay-outcache.

>[!NOTE]
>
>Voor Adobe Commerce op wolkeninfrastructuur 2.4.1 en recenter, kunt u het [ Plaats-brede Hulpmiddel van de Analyse ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access) gebruiken om automatisch te controleren als uw Volledig Geheime voorgeheugen van de Pagina niet correct wordt gevormd.

### Verwante lezing

[ het geheim voorgeheugenoverzicht van Adobe Commerce ](https://developer.adobe.com/commerce/frontend-core/guide/caching/) in onze ontwikkelaarsdocumentatie.
